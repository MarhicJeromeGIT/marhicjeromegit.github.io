---
author_profile: true
date: "2025-03-09T00:00:00Z"
title: First steps with CDK
---

Not much going on these days. At work, we started migrating some apps from Google App Engine to AWS, which gave me a chance to learn about [AWS CDK](https://docs.aws.amazon.com/cdk/v2/guide/home.html). As a learning step, I've made a small template to deploy a static website on S3 + CloudFront for the frontend and ALB + ECS for the backend, with some CloudFront behaviors, Route 53, and ACM certificates sprinkled in. As far as I know, it's a standard architecture (though I need to lock down the S3 permissions a bit more, add logs to CloudWatch, etc.), and it's really nice that it is reviewable by our security guy before we deploy it. And also, it can be deployed to staging first and later on to production with little to no changes.

In the past, I've been annoyed when writing a Lambda in staging and having to duplicate it in the production environment (a separate AWS account). This would solve those kinds of issues. Overall, I'm really pleased with the experience (especially given that the alternative was writing CloudFormation templates by hand or registering resources in the AWS console...). I didn't look too closely into the generated CloudFormation templates, but it's nice to be able to destroy and redeploy at will when something goes wrong.

A few gotchas that bit me before I got it to work:  
- First, I couldn't create a VPC because we were exceeding the "Elastic IP" limit (5 per account per the [AWS Doc](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html#using-instance-addressing-limit)), so I just reused an existing VPC.  
- I didn't have a health check endpoint in the backend code originally, so the service kept restarting and the deploy never completed successfully. We must have a `/health` (or `/`) endpoint reachable.  
- The ACM for CloudFront must be issued in "us-east-1"? That one was super bullshit.  

Given that I made my template during the weekend, I'm open-sourcing it here: [CDK Template](https://github.com/MarhicJeromeGIT/CDK-template) - the stack definition itself is [here](https://github.com/MarhicJeromeGIT/CDK-template/blob/master/cdk/lib/cdk-stack.ts). It deploys a single `index.html` page to S3 and CloudFront, registers some subdomains and SSL certificates, and deploys a load balancer and a container on ECS (using the `ApplicationLoadBalancedFargateService` construct) for a small Go app (a click counter).

