# 🚀 AWS URL Shortener  

## 📋 Project Overview  
This project implements a serverless URL shortening system using AWS services. The system enables users to create short URLs that redirect to original URLs with a configurable expiration time. It is designed to store the data efficiently and ensure the expiration time is validated before redirection.  

### ✨ Features  
- 🔗 Generates short URLs for user-provided original URLs.  
- 📂 Stores URL data (original URL and expiration time) in an S3 bucket.  
- ✅ Validates the expiration time of URLs before redirecting the user.  
- ☁️ Uses AWS Lambda functions to handle URL generation and redirection.  

---

## ⚙️ How It Works  
1. **🖍️ URL Generation Function:**  
   - Accepts the original URL and an expiration time via an API call.  
   - Generates a unique short URL code.  
   - Stores the short URL code, original URL, and expiration time in an S3 bucket as a JSON object.  

2. **🔄 Redirection Function:**  
   - Retrieves the short URL code and fetches the corresponding JSON object from S3.  
   - Validates the expiration time. If the URL has expired, returns an HTTP 410 status.  
   - If valid, redirects the user to the original URL with an HTTP 302 status.  

---

## 🏗️ Code Structure  

### `Main.java` (🛠️ URL Generation)  
- Handles API requests to create short URLs.  
- Generates unique short URL codes using UUIDs.  
- Stores URL data (original URL and expiration time) in S3 as JSON.  

### `Main.java` (🔗 Redirection)  
- Handles requests to redirect users using short URLs.  
- Validates the expiration time of the short URL.  
- Redirects to the original URL or returns an error if the URL has expired.  

### `UrlData.java`  
- Represents the URL data structure, including:  
  - 🌐 `originalUrl`: The original URL to redirect to.  
  - ⏰ `expirationTime`: The expiration time for the short URL in seconds since epoch.  

---

## 📦 Dependencies  
The project uses the following dependencies:  

- **🖥️ AWS Lambda Core** (`com.amazonaws:aws-lambda-java-core:1.2.1`): Provides core functionalities for AWS Lambda integration.  
- **📝 AWS Lambda Log4j2** (`com.amazonaws:aws-lambda-java-log4j2:1.4.0`): Enables logging capabilities in AWS Lambda.  
- **☁️ AWS SDK for S3** (`software.amazon.awssdk:s3:2.17.106`): Used for interacting with S3 buckets for data storage and retrieval.  
- **📄 Jackson Databind** (`com.fasterxml.jackson.core:jackson-databind:2.12.3`): Handles JSON parsing and serialization/deserialization.  
- **⚡ Lombok** (`org.projectlombok:lombok:1.18.34`): Reduces boilerplate code by generating getters, setters, constructors, etc.  

---

## 🔧 Plugins  
The project uses the following Maven plugin:  

- **📦 Maven Shade Plugin** (`org.apache.maven.plugins:maven-shade-plugin:3.2.4`): Packages the project and its dependencies into a single executable JAR file, suitable for AWS Lambda deployment.  

---

## 🛠️ Requirements  
- ☁️ AWS account with S3 and Lambda configured.  
- 🔧 Java SDK for AWS services.  
- 🛠️ Maven for dependency management and building the project.  
- 📄 JSON parser (Jackson library).  

---

## 🙌 Acknowledgements  
This project was developed as part of a free course offered by **Fernanda Kipper** on the **Rocketseat** platform. The course provided a hands-on experience with AWS and serverless technologies, focusing on practical implementation and learning.  

---
