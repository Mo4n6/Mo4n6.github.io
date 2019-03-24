---
layout: post
title: How to Create a Twitter App
date:   2018-11-03
description: Ever found that Tweeting is too much work and wanted to find a way to automate it? Well, I have good news for you. This article will walk you through how to make your first Twitter App with Python.  This is the first step in making your own AGI Twitter bot.
tags:
- Twitter
- Dev
- Python
share: true
toc: true
---

![img]({{ '/assets/images/2018-11-03-HowToCreateATwitterApp/image1.png' | relative_url }}){: .center-image }*Apply for Access*

# Introduction
This article will walk you through the steps to create a simple Twitter App using Python.

# Requirements
Prior to creating a Twitter App, you will need the following:

* Python 3.6 or later installed
* A Twitter Account

# Instructions
The steps to create a Twitter App is broken down into the following steps:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 1 - Apply for a Developer Account  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 2 - Create an App in Twitter  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 3 - Create Keys and Tokens for your App  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 4 - Install Python-Twitter Library  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 5 - Create a Python script that posts to Twitter   


## Step 1 - Apply for a Developer Account
You need to apply for a developer account through Twitter.  To do this, log in to Twitter and visit https://developer.twitter.com/

If this is your first time to log in to the above link, you would see something like this:

![img]({{ '/assets/images/2018-11-03-HowToCreateATwitterApp/image1.png' | relative_url }}){: .center-image }*Apply for Access*

Click on 'Apply for a Developer Account'.

![img]({{ '/assets/images/2018-11-03-HowToCreateATwitterApp/image2.png' | relative_url }}){: .center-image }*Application for Developer Account*

Review the instructions on the page.  Once ready to proceed, press on 'Continue'.  You will be asked some additional questions in regards to the developer account. You will need to complete 'Account Details' and 'Use case details'.

You will see something like this once you have answered all the questions and agreed to the Terms of Service.

![img]({{ '/assets/images/2018-11-03-HowToCreateATwitterApp/image3.png' | relative_url }}){: .center-image }*Confirmation Screen*


## Step 2 - Create an App in Twitter﻿
At this point, you've signed up for a Twitter Developer Account, confirmed you're email address and you're on the 'Get Started' Page.

![img]({{ '/assets/images/2018-11-03-HowToCreateATwitterApp/image4.png' | relative_url }}){: .center-image }*'Get Started' Page*

Click on 'Create an App' under 'Get started'.  You should see something like this:

![img]({{ '/assets/images/2018-11-03-HowToCreateATwitterApp/image5.png' | relative_url }}){: .center-image }*Create an app*

Click on ' Create an app' again.  You will be asked to fill out some information in regards to your app (similar to filling out the developer questionnaire).  Here are some of the details you will have to fill out:

![img]({{ '/assets/images/2018-11-03-HowToCreateATwitterApp/image6.png' | relative_url }}){: .center-image }*App questionnaire*

Complete the questionnaire to create your app.

## Step 3 - Create Keys and Tokens for your App
Now that you've created your Twitter App.  You will see something like this:

![img]({{ '/assets/images/2018-11-03-HowToCreateATwitterApp/image7.png' | relative_url }}){: .center-image }*App details*

Click on 'Keys and tokens'.  The Consumer API keys will be listed.  You will need also need to 'Create' the 'Access token & access token secret' for your App.

![img]({{ '/assets/images/2018-11-03-HowToCreateATwitterApp/image8.png' | relative_url }}){: .center-image }*App Keys and Tokens*

## Step 4 - Install Python-Twitter Library
This step will walk you through installing the Python-Twitter Library.  You will need to download the library from github.com.

Python-Twitter Library Link: https://github.com/bear/python-twitter

![img]({{ '/assets/images/2018-11-03-HowToCreateATwitterApp/image9.png' | relative_url }}){: .center-image }*Screenshot of Python-Twitter github library*

Download and extract the library.  Run the following command to install the library:
``` bash
python setup.py install﻿
```
The first time I tired to install the library, I got the following error message:
>error: The 'requests' distribution was not found and is required by python-twitter

![img]({{ '/assets/images/2018-11-03-HowToCreateATwitterApp/image11.png' | relative_url }}){: .center-image }*Screenshot of the installation error*

Running the install command again resolved the issue.

## Step 5 - Create a Python script that posts to Twitter
I know it's been fun, however we're almost at the end.  Now time to write a simple Python program that makes a post to Twitter.

Make sure to import twitter at top of your program:

{% highlight python linenos %}
import twitter
{% endhighlight python %}

Authenticate to Twitter by using your token, token secret, consumer_key and consumer_secret (from Step 3).  

{% highlight python linenos %}
api = twitter.Api(consumer_key=consumer_key, consumer_secret=consumer_secret,
access_token_key=token, access_token_secret=token_secret)
{% endhighlight python %}


Update your status with the following syntax:

{% highlight python linenos %}
status = api.PostUpdate("Hello World #HelloWorld #Python #TwitterApp")
{% endhighlight python %}

# Summary

Voila!! You've just sent a tweet!! Go check you're Twitter!!  You've made your first Twitter app with Python!!

This article provided the minimum steps required to create a Twitter App.  I know what you're thinking, this is a good start, but running a Python script to send a tweet still sounds like too much work.  In a future post I will show you how to use AWS lambda to make this more efficient and self reliant.
