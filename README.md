# Serverless Task Tracker Application using AWS

## 📌 Project Overview

The **Serverless Task Tracker Application** is a simple web-based application built using **AWS serverless services**. It allows users to securely log in, create tasks, and view a list of their tasks. The project demonstrates how frontend, backend, authentication, and database layers can be integrated without managing servers.

This project was developed as part of an **internship assignment** to understand and implement serverless architecture on AWS.

---

## 🏗️ Architecture Overview

The application follows a fully serverless architecture:

```
User (Browser)
   ↓
CloudFront (HTTPS)
   ↓
S3 (Static Frontend)
   ↓
Cognito (Authentication)
   ↓ JWT Token
API Gateway
   ↓
Lambda Functions
   ↓
DynamoDB
```

### AWS Services Used

* **Amazon S3** – Hosts static frontend files (HTML, CSS, JavaScript)
* **Amazon CloudFront** – Provides HTTPS access to the frontend
* **Amazon Cognito** – Handles user authentication and authorization
* **Amazon API Gateway** – Exposes REST APIs for backend operations
* **AWS Lambda** – Executes backend business logic
* **Amazon DynamoDB** – Stores task data

---

## 🔐 Authentication Flow

1. User accesses the frontend via CloudFront URL
2. User clicks **Login** and is redirected to Cognito Hosted UI
3. User signs up / logs in using email and password
4. Cognito generates a **JWT token**
5. User is redirected back to the frontend
6. Frontend uses JWT token to securely call backend APIs

---

## 🔄 Application Flow

### Login

* Authentication handled by **Amazon Cognito Hosted UI**
* Secure redirection using HTTPS (CloudFront)

### Create Task

* Frontend sends a POST request with task details
* API Gateway triggers **CreateTask Lambda**
* Lambda stores task data in DynamoDB

### View Tasks

* Frontend sends a GET request
* API Gateway triggers **GetTasks Lambda**
* Lambda retrieves tasks from DynamoDB and returns them

---

## 🧩 Backend APIs

### 1. Create Task API

* **Method:** POST
* **Endpoint:** `/tasks`
* **Function:** CreateTask Lambda
* **Description:** Creates a new task and stores it in DynamoDB

### 2. Get Tasks API

* **Method:** GET
* **Endpoint:** `/tasks`
* **Function:** GetTasks Lambda
* **Description:** Fetches all tasks from DynamoDB

API Gateway uses **Lambda Proxy Integration** to forward request data to Lambda functions.

---

## 🎥 Demo

[![Watch the demo](https://img.youtube.com/vi/LHUnN11YYYo/0.jpg)](https://youtu.be/LHUnN11YYYo)

---

## 🗄️ Database Design

**DynamoDB Table:** `Tasks`

| Attribute | Type   | Description        |
| --------- | ------ | ------------------ |
| taskId    | String | Primary key (UUID) |
| taskName  | String | Name of the task   |

---

## 🚀 Deployment Summary

* Frontend deployed to **S3** and served via **CloudFront**
* Backend deployed using **Lambda** and **API Gateway**
* Authentication implemented using **Cognito User Pools**
* Database managed by **DynamoDB**

All components are managed services, enabling automatic scaling and reduced operational overhead.

---

## ✅ Key Learnings

* Understanding serverless architecture
* Integrating frontend and backend using AWS services
* Implementing secure authentication using JWT tokens
* Using API Gateway to trigger Lambda functions
* Managing data using DynamoDB

---

## 🏁 Conclusion

This project demonstrates a complete **end-to-end serverless application** on AWS. It highlights how modern cloud-native applications can be built securely, scalably, and efficiently without managing servers.

---

**Author:** GC

**Tech Stack:** AWS S3, CloudFront, Cognito, API Gateway, Lambda, DynamoDB
