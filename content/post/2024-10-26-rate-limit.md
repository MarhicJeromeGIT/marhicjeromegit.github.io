---
author_profile: true
date: "2024-10-26T00:00:00Z"
title: Rate Limit
---

In this post, we'll discuss various common ways of handling API rate limits, and I'll introduce a new tool I've been working on called [MeterFlow](https://github.com/goverture/meter_flow).

Most APIs have rate limits, usually counted in requests per minute, but other resources can be limited as well (for instance, the number of characters you can translate with the Google Translate API, or the number of tokens you can generate with some LLM API). When you exceed the rate limit, the API will return a 429 status code, telling you to slow down. There are various ways of dealing with API rate limits in your code.

### 1. Ignore it

Some API rate limits are pretty high, and you might not need to worry about them too much if you know your usage is low. For instance, the Google Translate API has a 6 million characters, 300,000 requests per minute [quota](https://cloud.google.com/translate/quotas). If it is unlikely you are ever going to translate this much (at $20 per million characters, you would be spending $120 per minute!), you may have ignored the rate limit so far with no consequence.

### 2. Sleep on it

An easy method is to retry the request a couple of times, with some sleep time in between. Simple Ruby pseudo-code:

```ruby
retry_count = 0
begin
  response = make_request()
rescue Faraday::ClientError => e
  if e.response[:status] == 429 && retry_count < MAX_RETRY_COUNT
    retry_count += 1
    sleep 2 ** retry_count # exponential backoff
    retry
  else
    raise
  end
end
```

The request might succeed on the second or third try if the rate limit was reached temporarily due to a short burst of traffic. An alternative to sleeping is to raise an error and rely on Sidekiq's retry mechanism to handle the retry.

In their [cookbook](https://cookbook.openai.com/examples/how_to_handle_rate_limits#proactively-adding-delay-between-requests), OpenAI suggests adding a delay proactively (sleeping before making the call), but it's not ideal either (you are still paying for this CPU time!).

### 3. Infrastructure rate limit

If you are performing the API calls in the background (things like a Sidekiq job), you can limit the number of concurrent jobs (either with the number of processes/threads, or by making a [capsule](https://github.com/sidekiq/sidekiq/blob/main/docs/capsule.md)). For instance, if you are running 10 threads and each job takes at least 5 seconds to run, you know you won't exceed 120 calls per minute to your external service.

### 4. Introducing MeterFlow

These solutions are not ideal: 1 and 2 can lead to failed requests, and 3 breaks anyway if you are calling the same API across multiple services (for instance, using an LLM endpoint to perform various tasks in separate microservices). Also, it is not easy to set a lower bound on your job execution time, so you'd have to account for some safety margin, leading to underutilization of your infrastructure. And anyway, you don't want to run thousands of jobs and have them retry or sleep; ideally, you want to schedule them to run at the appropriate time.

This is where [MeterFlow](https://github.com/goverture/meter_flow) comes in. It is a simple, open-source service that can schedule your API calls, taking into account the current usage of the resource and the corresponding rate limits. The usage is simple: register a resource, then schedule calls to it. MeterFlow will return the delay before each call should be made.

```ruby
# Step 1: Request the schedule from MeterFlow
uri = URI("http://localhost:8080/schedule")
response = Net::HTTP.post(
  uri,
  { resource_name: 'dummy_api', num_calls: 1000 }.to_json,
  "Content-Type" => "application/json"
)

# Step 2: Parse the response and enqueue jobs based on the delay
delays = JSON.parse(response.body)['delays']
delays.each_with_index do |delay, index|
  DummyApiCallWorker.perform_in(delay, index + 1)
end
```

If all the API calls to a given resource across your organization are scheduled by MeterFlow, you can be sure you won't exceed the rate limit. Planned features include support for multiple limits per resource (for instance, calls per minute + characters per hour, etc.) and Prometheus data export for monitoring.

