# Blitz 1: URL Shortening Application Optimization

## Overview

Nike raised concerns about extended webpage loading times on our Python URL Shortening application deployed on AWS Elastic Beanstalk. Customers reported high latency issues. To assess the problem, a load test was conducted using (Apache JMeter)[https://jmeter.apache.org/] to simulate 1000 HTTP GET requests to the application deployed on AWS Elastic Beanstalk. This highlighted the need to optimize the application's performance.

<img width="448" alt="Screen Shot 2023-09-29 at 5 16 40 PM" src="https://github.com/belindadunu/Blitz1/assets/139175163/f3bff27e-dd06-4f3c-be56-4e5d52a7d30f">

## Investigation

### What Happened During the Blitz?

The JMeter load test revealed a server latency of 40 milliseconds for user requests to the application on Elastic Beanstalk, indicating optimization was required.

<img width="299" alt="Screen Shot 2023-09-30 at 5 03 35 AM" src="https://github.com/belindadunu/Blitz1/assets/139175163/f48efd55-1c2e-4f30-b3f2-5edf63b42e7f">

### What Did You Do to Resolve the Issue?

To resolve the high latency problem, an Amazon CloudFront CDN was integrated. By leveraging Amazon’s global edge servers, static content was efficiently delivered to users. This reduced the average from 40ms down to just 9ms - a 4x improvement. The CDN stored frequently accessed URLs and webpage HTML files, further enhancing the user experience.

In scenarios where the CDN couldn't fulfill requests, they were routed to the web server. However, the overall average latency still decreased substantially due to CDN implementation. For optimal results, all static content should be uploaded to the CDN, bypassing the web server and backend infrastructure for faster response times.

<img width="286" alt="Screen Shot 2023-09-29 at 5 16 50 PM" src="https://github.com/belindadunu/Blitz1/assets/139175163/fe4863d0-7296-4296-961d-4b5f8bf9124e">


### What Was the Purpose?

Blitz 1 demonstrated the effectiveness of a content delivery network in reducing web application latency. Storing and serving content from edge locations closer to users significantly cut request fulfuillment time. This ensured swift access to webpages, improving overall user experience. 

### Recommendations

We could also use ping tests and browser dev tools to check the improvements. Dev tools show how long each file takes to load. Ping gives you the latency between point A and B. Using these along with load tests would help keep monitoring optimizations and catch any new issues. We'd get alerts if new slowdowns popped up. Then we could jump back in to speed things up again.

## Diagram

### Before and after Blitz 1:

![Blitz1 drawio](https://github.com/belindadunu/Blitz1/assets/139175163/5603abc8-325d-4044-949a-24dc4145bdd7)
