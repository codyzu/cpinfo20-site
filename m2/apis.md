---
title: Module 2 - APIs
redirect_from: /m2
---

# 🤖 Module 2: APIs

In this module we will practice calling APIs.

When building a web application, you will most certainly need to call some APIs.

* **API** - **A**pplication **P**rogramming **I**nterface
* **REST** - **RE**presentational **S**tate **T**ransaction

**💡Tip: You can either test the APIs with Chrome or wth [Postman](https://www.getpostman.com/) (download from the instructor).**

## 1 OpenWeather ⛈ API

[OpenWeather](https://openweathermap.org/) is service providing APIs providing weather forecasts.

The OpenWeather [One Call API](https://openweathermap.org/api/one-call-api) provides a 7 day weather forecast. The free account allows 1000 requests per day!

### 1.1 Sign up for OpenWeather API
1. Go to https://home.openweathermap.org/users/sign_up and signup for a new account.
1. Confirm your account with the email you received.
1. Login to your account.

### 1.2 Call OpenWeather API
1. Go to your [API keys](https://home.openweathermap.org/api_keys) page and copy your default API key.
   ![OpenWeather API key](./images/openweather-api-key.png)
1. Go the the [One Call API documentation](https://openweathermap.org/api/one-call-api) page and copy one of the sample API calls.
   ![OpenWeather Sample API call](images/openweather-sample.png)
1. Test the API call.
   1. In Chrome or Postman, replace `{API key}` with the API key you copied in the previous step.
   1. Add `&lang=fr&units=metric` to the URL to format the data into French.
   1. Remove the portion of the URL `&exclude=hourly,daily` to see all of the data. The `daily` data will be ideal to build our weather application. We could then add `&exclude=minutely,hourly` to see only the daily and current data.
   1. Annecy has a latitude of `45.89911` and longitude of `6.1287`, update your request to get the weather for Annecy.
1. Note your _API key_ for later.

## 2 Here geocoding 🌐 API

The OpenWeather API accepts an exact latitude and longitude coordinate for the weather forecast. If we want to get the weather forecast for location, like `Annecy` or `Lyon`, we need a way to get the geographic latitude and longitude for locations. This is called **geocoding**.

[Here](https://www.here.com/) offers several location tools, including a **geocoding API**. With their freemium plan we can make 250000 requests per month for free.

### 2.1 Sign up for Here
1. Go to https://developer.here.com/sign-up?create=Freemium-Basic and signup a freemium account.
1. Accept the conditions and click _Start coding_.
   ![here signup](images/here-signup.jpg)
1. ⚠️ Verify your email in the received email message. _This is important to ensure your API keys don't expire!_
1. Click the button _Generate App_ under the **REST** section.
   ![here generate app](images/here-generate-app.png)
1. Click on the button _Create API key_.
   ![here generate api key](images/here-generate-keys.png)
1. Once the keys are generated, copy the `API KEY`:
   ![here api key](images/here-key.png)

### 2.2 Call Here API
1. The [here geocode api documentation](https://developer.here.com/documentation/geocoder/dev_guide/topics/quick-start-geocode.html) shows how we can make an api request.
1. Open https://geocoder.ls.hereapi.com/6.2/geocode.json?apiKey={YOUR_API_KEY}&searchtext=annecy+france to see the geocode results for `Annecy, France`.
1. Look into the response to find the `NavigationPosition` `Latitude` and `Longitude`.

#### Exercise 2.1: What is the Latitude and Longitude of Lyon?

#### Exercise 2.2: What is the Latitude and Longitude of your home address?