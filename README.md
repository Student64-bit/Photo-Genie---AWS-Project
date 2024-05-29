## Photo Genie
# Overview

This project is a simple frontend application that acts as a genie, identifying images posted by users using various Amazon Web Services (AWS).

## AWS Services Used

- **AWS API Gateway:** Invokes a Lambda function upon receiving an API call from the frontend.
- **AWS Lambda:** Calls Rekognition to identify image labels.
- **AWS S3 Storage:** Stores user-submitted images from the frontend for processing.
- **AWS Rekognition:** Identifies and labels user-submitted images.
- **AWS CloudWatch:** Aids in troubleshooting and logging activities.
- **AWS Cloud9:** Provides an integrated development environment (IDE) with multiple SDKs like Python, PHP, and more.

## Other Services Used

- **HTML:** Serves as a basic frontend where users can submit images.

## Project Architecture

<p align="center">
  <img src="https://i.imgur.com/WnnBdnl.png" alt="Architecture Diagram" width="80%" height="80%">
  <br>
  <strong><small>Figure 1: Simple Architecture Diagram.</small></strong>
</p>

## Project Steps

### 1. Utilizing and Understanding AWS Cloud9

I usually use Visual Studio Code (VSCode), so I decided to try AWS Cloud9, an AWS service that provides a development environment or IDE with various SDKs like Python, PHP, and more.
<p align="center">
  <img src="https://i.imgur.com/l40iUU2.png" alt="Code commit permissions" width="80%" height="80%">
  <br>
  <strong><small>Figure 2: Running Python code in Cloud9 IDE to obtain Rekognition labels for an item stored in S3.</small></strong>
</p>
<br>


### 2. Changing the Architecture and Adding Software as a Service (SaaS)

Originally, the infrastructure was set up to scan an S3 bucket with Rekognition to label or identify an image. However, to enhance user accessibility and incorporate SaaS, I added a frontend where users can submit images. This change allows the API Gateway to invoke a Lambda function, which calls Rekognition to identify the image, instead of manually uploading the photos to S3.

<p align="center">
  <img src="https://i.imgur.com/2wUU82E.png" alt="Code commit permissions" width="80%" height="80%">
  <br>
  <strong><small>Figure 3: SaaS frontend added to improve user accessibility.</small></strong>
</p>
<br>



### 3. How Everything Works Together

Here’s an overview of the process: A user interacts with the HTML frontend to submit images. Once an image is submitted, a 'POST' request is made by API Gateway, which uploads the image to an S3 bucket and calls Rekognition. Rekognition then identifies the objects in the image and provides labels, which are sent back to the frontend, giving the user an idea of what Rekognition thinks the image contains.

### 4. CloudWatch for Troubleshooting

CloudWatch was extremely helpful for troubleshooting. Initially, I encountered 500 errors in the console logs. By delving deeper into the logs, CloudWatch helped me identify that the issue was due to insufficient permissions for the Lambda function in API Gateway.

<p align="center">
  <img src="https://i.imgur.com/xXRMuAG.png" alt="Code commit permissions" width="80%" height="80%">
  <br>
  <strong><small>Figure 4: Cloudwatch logs helping me identify an issue.</small></strong>
</p>
<br>

<p align="center">
  <img src="https://i.imgur.com/J00Ur4j.png" alt="Code commit permissions" width="80%" height="80%">
  <br>
  <strong><small>Figure 5: Using postman to check if API Gateway is operating as intended.</small></strong>
</p>
<br>

### 5. Project Video Demo
[View the video demo here](https://youtu.be/TKk2ifd-FBU).


