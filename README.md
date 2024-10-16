# Scalable Video Streaming Service on AWS

## Project Overview

This project focuses on building a **scalable video streaming service** utilizing cloud infrastructure. The application is designed to ensure high availability, performance, and secure delivery of media content. It leverages **AWS services** like S3, EC2, MediaConvert, and CloudFront to handle video storage, transcoding, and global distribution.

## Key Features

- **Scalable Storage:** Utilizes Amazon S3 buckets for storing original and transcoded video content.
- **Transcoding:** Converts original video files to 720p using an EC2 instance for optimal streaming quality.
- **Global Content Delivery:** AWS CloudFront is used as a CDN (Content Delivery Network) to ensure fast and reliable content delivery.
- **High Availability:** Ensures that the application can scale with demand using Auto Scaling on custom AMIs.
- **Secure Access:** Provides secure access through HTTPS, AWS IAM roles, and proper bucket policies.
  
## Architecture

1. **Amazon S3:** 
   - Bucket 1: Stores original video files.
   - Bucket 2: Stores transcoded 720p video files.
   - Bucket 3: Hosts the frontend of the streaming service.
   
2. **EC2 Instance:**
   - Used for transcoding original videos into 720p format.
   - Ubuntu EC2 instance configured with MediaConvert for video transcoding.
   
3. **AWS CloudFront:**
   - Configured to serve videos globally from the transcoded S3 bucket.
   - Optimized caching for reduced latency and faster video delivery.

4. **IAM Roles:**
   - Provides permissions for EC2 instances to access and manage S3 buckets.
   
5. **Frontend Hosting:**
   - A simple frontend is hosted on S3 and served via CloudFront for streaming video content.

## Project Workflow

1. **Step 1: Create S3 Buckets**
   - Bucket 1: Original videos.
   - Bucket 2: Transcoded videos (720p).
   - Bucket 3: Frontend hosting.

2. **Step 2: Setup EC2 Instance for Transcoding**
   - Launch an EC2 instance (Ubuntu) and configure it for transcoding using FFMPEG or MediaConvert.
   - Transcode videos from Bucket 1 (original) to Bucket 2 (transcoded).

3. **Step 3: Setup CloudFront for Video Delivery**
   - Configure CloudFront with S3 Bucket 2 (transcoded videos) as the origin.
   - Enable caching and HTTPS for secure and fast content delivery.

4. **Step 4: Host Frontend via S3 and CloudFront**
   - Develop a simple frontend for video streaming and host it on Bucket 3.
   - Use CloudFront to serve the frontend globally.

5. **Step 5: Setup Apache on EC2 for S3 Access**
   - Install and configure Apache on the EC2 instance to serve the video content.
   - Attach IAM roles to allow EC2 instances to access S3 buckets.

6. **Step 6: Testing and Deployment**
   - Test the video streaming service using CloudFront's domain.
   - Create a custom AMI from the EC2 instance and configure Auto Scaling for high availability.

## Tech Stack

- **AWS Services:** S3, EC2, CloudFront, MediaConvert, IAM, Auto Scaling
- **Frontend:** Basic HTML/CSS (React/Vite for advanced setup)
- **Transcoding:** MediaConvert / FFMPEG on EC2
- **Operating System:** Ubuntu 20.04 (on EC2)
- **Web Server:** Apache

## How to Run the Project

1. Clone this repository:
   ```bash
   git clone https://github.com/network-nakul/video-streaming-service.git
   cd video-streaming-service

1. **Set up your AWS environment and create the necessary S3 buckets.**

2. **Launch an EC2 instance and configure it for transcoding using the `setup-ec2-transcoding.sh` script.**

3. **Upload original video files to the S3 bucket and start the transcoding process using the EC2 instance.**

4. **Configure CloudFront to serve the transcoded videos from the second S3 bucket.**

5. **Deploy the frontend to S3 and test the service using the CloudFront domain.**

## Future Enhancements

- **Live Streaming**: Implement live streaming capabilities using AWS Elemental MediaLive.
- **User Authentication**: Add user login and authentication using AWS Cognito.
- **Advanced Frontend**: Upgrade the frontend with a full-fledged React or Vite-based user interface.

## Contact

- **Email**: [network.nakulgaur@gmail.com](mailto:network.nakulgaur@gmail.com)
- **LinkedIn**: [Nakul Gaur](https://www.linkedin.com/in/nakul-gaur/)
