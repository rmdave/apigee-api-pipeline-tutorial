# Purpose

This repo is focused on providing an overview of the Apigee API
proxy processing pipeline and provide clarity to the following
buzzwords:


![Alt text](./images/ApigeeWordCloud.png?raw=true "ApigeeWordCloud")


This is a working demo to highlight the API Proxy processing pipeline and 
is not a production quality product.  The demo will map the processing 
pipeline stages and keywords with existing Apigee assets that provide
additional context.

Pull request welcomed but please keep in mind the spirit of this repo.
Feedback is always solicited!


## So, what do we have here?

This demo simulates an enterprise's need to expose two 
services that have their own 
limitations, keys and caching requirements.

The OpenWeatherMap and FourSquare services are used to 
simulate the enterprise's two
services.
 
## Pre-reqs

You are expected to know how to get around the Apigee UI,
and how to use PostMan to make API requests.

The links below will get you keys and accounts but you will have to 
read their documentation to get a fundamental understanding of 
their services.

Signup for OpenWeatherMap and FourSquare developer programs so that you can invoke
these endpoints:

http://api.openweathermap.org/data/2.5/weather
https://api.foursquare.com/v2/venues/explore


Sign up for Google Apigee's generous free developer account:

https://apigee.com/api-management/#/homepage

Get PostMan so that we can issue API calls:

https://www.getpostman.com/
<hr>

# Exercises

## Access the services directly

Use Postman and access the services directly to ensure that you have the correct keys 
and API call formats working.


## Introduction - What will we have at the end

This video shows you what we will have at the end of this
exercise.

### Video

https://youtu.be/trqzaR-UBRI


##  Step 2

We will:
 
- Make a request directly from a client
- Setup an API Proxy for OpenWeather
- Invoke OpenWeather via Apigee

### Video

- https://youtu.be/uKQ-WOsDsDQ

### Apigee assets 
The following Apigee assets will help in accomplishing
the above:

https://docs.apigee.com/api-platform/fundamentals/understanding-apis-and-api-proxies
https://docs.apigee.com/api-platform/fundamentals/build-simple-api-proxy

##  Step 3 - Implement two targets and proxy endpoints

We will:
 
- Setup two target endpoints to route requests to the associated internal service.
- Setup two proxy endpoints i.e. URLs exposed to the internet by the enterprise
- Invoke the weather API via Apigee with minimal processing within Apigee.  This will work but not as intended
- We will implement a resource guard using a RaiseFault policy to 'catch all' 
invocations that don't match the URI paths implemented

### Video
- https://youtu.be/9eUlIWTzqio
- Resource guard - https://www.youtube.com/watch?v=GXX8omcWTHU&feature=youtu.be

### Apigee assets 
The following Apigee assets will help in accomplishing
the above:

- https://docs.apigee.com/api-platform/fundamentals/understanding-apis-and-api-proxies
- https://docs.apigee.com/api-platform/fundamentals/build-simple-api-proxy

## Step 4 - Conditional Flows
This video will cover how the traffic to the internal 
service is directed with the use of Apigee's 
conditional flows. 

We will:

- Make API calls
- Add policies to the conditional flows to adjust the URLs invoked by 
Apigee on the target servers
- Implement a RouteRule to direct traffic to the 4SQ server


### Video
- https://youtu.be/sPTyeU1FGes

### Apigee assets

- https://docs.apigee.com/api-platform/fundamentals/what-are-flows
- https://docs.apigee.com/api-platform/fundamentals/understanding-routes



## Step 5 - Response Cache
Let's add caching to take the load off the services.

- Add ResponseCache policies 
- Move ResponseCache Policy to a conditional Flow
- Apigee caches the response but the ResponseCache policy needs to be correctly
implemented within the API processing pipeline

### Video (verified)
- https://youtu.be/2tnUZ2sfSbI

### Apigee Assets

- https://docs.apigee.com/api-platform/reference/policies/response-cache-policy
- https://www.youtube.com/watch?v=TUBGNxUCp7w&feature=youtu.be

## Step 6 - Conditional flows on the TargetEndpoint Response Flow
Let's correctly implement the ResponseCache policies since the caching requirements
for 4SQ and OpenWeather are different.

- Move ResponseCache policy to correct response flow 
- Implement the ResponseCache correctly (cache GET responses only)

- Link to video

### Apigee Assets





# Summary And What's wrong with this demo

You would make a lot of changes to make this into production code.
Some of them are:

1. This demo is almost a pass through demo (Keys for backend services
are in the request from the client) and you would change that.
1. RaiseFault policies to handle issues
1. KVM policies to extract keys from Apigee KVM stores based on environment
1. Input parameter checks
1. Much more...

Please use this repo as an educational asset only.

### Video

https://youtu.be/vRcCB1SScPI



