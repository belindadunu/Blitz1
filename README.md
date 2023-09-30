# Blitz 1: URL Shortening Application Optimization

## Overview

Nike raised concerns about extended webpage loading times on our Python URL Shortening application deployed on AWS Elastic Beanstalk. Customers reported high latency issues, prompting a detailed investigation to optimize the application's performance.

## Investigation

### What Happened During the Blitz?

To assess the issue, a load test was conducted, simulating 1000 GET requests to the application deployed on AWS Elastic Beanstalk. The test revealed a server latency of 40 milliseconds for user requests, indicating a need for optimization.

### What Did You Do to Resolve the Issue?

To resolve the latency problem, an Amazon CloudFront CDN was integrated. By leveraging Amazon’s global edge servers, static content was efficiently delivered to users, reducing the latency to 9ms. The CDN stored frequently accessed URLs and webpage HTML files, enhancing the user experience significantly.

In scenarios where the CDN couldn't fulfill requests, they were routed to the web server. However, the overall average latency decreased due to CDN implementation. For optimal results, all static content should be uploaded to the CDN, bypassing the web server and backend infrastructure for faster response times.

### What Was the Purpose?

Blitz 1 showcased the potential of a content delivery network in reducing web application latency. By storing and serving content from locations distant from the application's servers, user experience was dramatically improved, minimizing request fulfillment time and ensuring swift access to webpages.

## Diagram

### Before Blitz 1:

![Blitz1 drawio](https://github.com/belindadunu/Blitz1/assets/139175163/5603abc8-325d-4044-949a-24dc4145bdd7)
