---
author_profile: true
date: "2025-01-02T00:00:00Z"
title: And a Happy New Year! (2025)
---

Looking back, 2024 was a pretty good year across all metrics! Learned new things at work even though it's my 5th year at the job, been pretty healthy and fit, not been drinking much (was a dry NYE, and will be doing a dry January). So I'm not taking any big resolutions for this year; it should be plenty busy already with the birth of my second kid in a few months. I'll just try to finish and release my crossword generator application before that, and that will be it. Maybe try to be more smiley and relaxed in general.

Over the holidays, I've made some progress on that crossword app. I've been mostly focused on reducing the memory footprint. The original implementation used more than 30GB for a 15x15 grid; I've managed to reduce it to about 5GB — first by using a sparse matrix, then by ditching the matrix altogether and generating rows one by one. I was wondering what the Go equivalent for Ruby's "yield" would be. I wanted something like this:

```ruby
def generate_data
  (1..10).each do |i|
    yield i
  end
end

def process_data(data)
  puts data
end

generate_data do |data|
  process_data(data)
end
```

Go channels are really convenient for this:

```go
dataChan := make(chan int) // could be buffered or not

go func() {
    defer close(dataChan)

    for i := 0; i < 10; i++ {
        dataChan <- i
    }
}()

for i := range dataChan {
    println(i)
}
```

It's clean, and actually even better because the next data point can be generated concurrently while the current one is being processed.

Another stretch goal of mine is to complete [Baba is You](https://hempuli.com/baba/). I've been at it for the past few months already, usually playing one or two levels before sleeping. It's a nice feeling of achievement to see the "Congratulations" banner before going to bed, and as is often the case with brain stuff, if I get stuck at night, I can usually solve it the next day. With all the AGI talk and the recent [ARC-AGI achievements by OpenAI's O3 model](https://arcprize.org/blog/oai-o3-pub-breakthrough), I've been thinking that I would personally consider AGI reached if a model could solve any random Baba is You level, with all the "thinking outside the box" required. I think the current "test-time compute" approach is appropriate here; it should be possible to have an LLM generate ideas and a verifier checking what the result of a given action is.

