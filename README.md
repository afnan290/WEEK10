# WEEK10
# MERN Blog App Deployment on AWS

This repository contains a complete solution for deploying a MERN stack blog application using AWS free-tier services.

## Contents

- MongoDB Atlas Configuration (Optional)
- S3 Bucket for Frontend
- S3 Bucket for Media Uploads
- IAM User and Policy for S3 Media Access
- EC2 Backend Setup

## MongoDB Atlas Configuration
1. Create an account on MongoDB Atlas.
2. Set up a free (M0) cluster.
3. In "Network Access", add your EC2 instance IP or 0.0.0.0/0.
4. In "Database Access", create a new user with read and write privileges.
5. Copy the connection string and update config/backend.env.

## S3 Bucket for Frontend
1. Create a bucket named yourname-blogapp-frontend in region eu-north-1.
2. Disable "Block all public access".
3. Enable Static Website Hosting.
4. Add the following bucket policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::yourname-blogapp-frontend/*"
    }
  ]
}
