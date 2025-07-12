# Reachitecturing-Java-Web-app-on-AWS

## Overview

This project demonstrates a modern, cloud-native architecture for a Java web application using AWS managed services. The solution is designed for scalability, high availability, global performance, and robust security.

---

## Architecture Flow

1. **User Access & DNS Routing**
    - Users access the web application via a custom domain managed by **Amazon Route 53** connected to godady.
    - **Route 53** intelligently routes requests to **Amazon CloudFront** (CDN), ensuring global, low-latency access.

2. **Content Delivery & Load Balancing**
    - **CloudFront** delivers static and dynamic content from the edge location closest to the user.
    - Requests are forwarded to an **Application Load Balancer (ALB)** within **AWS Elastic Beanstalk**.

3. **Application Hosting**
    - **Elastic Beanstalk** automates deployment, scaling, and management of the Java application (built with Maven and running on Apache Tomcat).
    - **Auto Scaling Groups** handle fluctuating traffic by automatically adding or removing instances.
    - Application artifacts (WAR/JAR files) get bult by following ci/cd pi[peline procedure with maven 

4. **Monitoring & Observability**
    - **Amazon CloudWatch** provides centralized logging, metrics, dashboards, and alerts for all components.

5. **Backend Integration**
    - **Amazon MQ (RabbitMQ):** Manages asynchronous messaging between microservices and app components.
    - **Amazon ElastiCache (Memcached):** Offers in-memory caching for fast data access and reduced database load.
    - **Amazon RDS (MySQL):** Provides a scalable, managed relational database.

6. **Security**
    - All communications and access are protected by **VPC Security Groups** and **IAM roles** with least-privilege permissions.

