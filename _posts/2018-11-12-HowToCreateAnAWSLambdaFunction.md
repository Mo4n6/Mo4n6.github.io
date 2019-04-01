---
layout: post
title: How to Create an AWS Lambda Function
date:   2018-11-12
description: What's cooler than a Twitter App that runs on your laptop and sends tweets?  A Twitter App that runs in the cloud and tweets based on a pre-defined schedule.  This article will not only save you money on your electricity bill, it will walk you through how to create a Lambda function.

tags:
- AWS
- Lambda
- Dev
- Python
share: true
toc: true
---

---

![img]({{ '/assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image1.png' | relative_url }}){: .center-image }*AWS Lambda*

---
# Introduction
This article will walk you through how to create an AWS Lambda Function.  An AWS Lambda Function consists of a Trigger, Function and Resources.The Trigger will be generated based on an event.  An example of an event that is a 'CloudWatch Event'.  The 'CloudWatch Event' can be configured to generate a trigger based on a specified schedule.  The Function will be executed once an event is triggered.  We will go into more details later.

![img]({{ '/assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image3.png' | relative_url }}){: .center-image }*Designer Window*

The function can be written in  different programming languages.  Here is a list of these languages:

![img]({{ '/assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image2-2.png' | relative_url }}){: .center-image }*AWS Lambda Runtime Frameworks*

# Instructions
The process to create a Lambda Function is broken down into the following steps:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 1 - AWS account overview  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 2 - Create a Lambda function  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 3 - Add Trigger from 'CloudWatch Event'
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 4 - Create the handler function
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 5 - Zip your code and upload it
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Step 6 - Configure test event and test

## Step 1 -  AWS account overview

You will need to sign up for an AWS Account.  The sign up process will require you to enter Credit Card information.  There are different tiers for an AWS account.  With the 'Free Tier' you can run 1M Requests per Month and 400,000 GB-seconds of compute time per month.

Links:
[Console AWS](https://console.aws.amazon.com/)
[AWS Lambda Pricing](https://aws.amazon.com/lambda/pricing/)


## Step 2 - Create a Lambda function

Now that you've signed up for an AWS account, you're ready to create a Lambda function.

From 'Services' Menu select 'Lambda'.

![img]({{ '/assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image4.png' | relative_url }}){: .center-image }*AWS Services*

Click on ' Create a function'.  Select 'Author from scratch'.

![img]({{ '/assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image5.png' | relative_url }}){: .center-image }*Create a function 1*

Fill in the 'Name' of the function, Runtime, Role and Role Name.

![img]({{ '/assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image6.png' | relative_url }}){: .center-image }*Create a function 2*

Roles are created based on the permissions that you want to grant to your AWS Lambda function.

AWS Lambda Permissions Model can be reviewed at https://docs.aws.amazon.com/lambda/latest/dg/intro-permission-model.html#lambda-intro-execution-role

## Step 3 - Add Trigger from 'CloudWatch Event'

Once you created your function, you will see something like this.  Click on 'CloudWatch Events' on the left tool bar.

![img]({{ '/assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image7.png' | relative_url }}){: .center-image }*Create a function 2*

Configure the trigger by configuring a new Rule.  You can use cron or rate expressions to configure the rule.  Here the rule is configured with cron (0 13 * * ? *) to run daily at 13:00 GMT.

Link for additional details on Cron Expressions:
[Cron Expressions](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/ScheduledEvents.html#CronExpressions)


![img]({{ '/assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image8.png' | relative_url }}){: .center-image }*Creating a Trigger*

Save your function after configuring the Trigger Rule.  You will see something like this:

![img]({{ '/assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image9.png' | relative_url }}){: .center-image }*Cron Expression Trigger*

## Step 4 - Create the handler function

Your code needs to contain a lambda event handler.  The name of the event handler function needs to be configured in the AWS Web GUI.  This is shown below:

![img]({{ '/assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image10.png' | relative_url }}){: .center-image }*Lambda Handler Function*

The code for the event handler looks something like this:

{% highlight python linenos %}
import json
def lambda_handler(event, context):

# TODO implement
return {
  'statusCode': 200,
  'body': json.dumps('Hello from Lambda!')
}
{% endhighlight python %}

Your code will need to include a handler similar to above.  The #ToDo implement can be replaced with main(), if you have a main() function defined in your code.

## Step 5 - Zip your code and upload it

Now that your code is ready.  There is one more step prior to creating a zip file.

Any 3rd party libraries that your code imports needs to be included in the .zip file.

For example, if your code imports Python-twitter libraries, you will need to install the libraries in the code directory.  This can be done with the following command executed from your code directory:

Windows:
```
pip install python-twitter -t .
```

Linux:
```
pip instaall python-twitter -t $(pwd)
```

After the code directory includes all the 3rd party libraries and the code, you need to create a .zip file that includes everything.  The .zip file may look something like this.

![img]({{ '/assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image11.png' | relative_url }}){: .center-image }*Lambda function .zip file*

Now upload the .zip file to the Lambda function.

![img]({{ '/assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image12.png' | relative_url }}){: .center-image }*Upload .zip file*

## Step 6 - Configure test event and test
Now you have created a trigger and uploaded your code, you're ready for testing.

Click on 'Test' button to create a test event.

![img]({{ '/assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image13.png' | relative_url }}){: .center-image }*Test*

Here is how the test event creation may look like:

![img]({{ '/assets/images/2018-11-12-HowToCreateAnAWSLambdaFunction/P2-Image14.png' | relative_url }}){: .center-image }*Create test event*

You can configure the test event based on the scenario you want to test.  If your code doesn't require any input parameters, you can click on 'Create' to test your code.  Make sure to 'Save' your function periodically.

# Summary
You're done!!! Good Job, you've created a lambda function.  Here are some things that you might of done if you followed through with the article:

* Setup and configured your 'free tier' AWS account.
* Created an AWS Lambda Function.
* Added a 'CloudWatch Event' to trigger your function once a day.
* Added an event handler function to your code to handle the trigger from the 'CloudWatch Event'.
* Installed 3rd party libraries in your code directory.
* Created a .zip archive for your code and uploaded it.
* Created a Test event to test out your code.

In a future article I'll touch base on how to do this with AWS SAM (Serverless Application Model) CLI.
