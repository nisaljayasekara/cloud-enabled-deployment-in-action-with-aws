

# Cloud-Enabled Deployment on Google Cloud Platform (GCP)

**Name:** Nisal Jayasekara  
**Student ID:** 2301682030  
**Email:** j.nmjayasekara@gmail.com 
Video Recording : https://drive.google.com/file/d/1IfEsIvppwCIHSGJ1MUgcY4YOZEAcWrRg/view?usp=sharing


## Project Overview

This project implements a cloud-native microservices architecture on GCP, featuring three backend services and a React frontend. It highlights modern cloud deployment practices, including managed databases, serverless computing, and cloud storage.

## Services

1. **Course Service (Google Cloud SQL - MySQL)**
   - **Database Engine:** MySQL 8.0.41
   - **Instance Tier:** db-f1-micro (1 vCPU, 3.75 GB RAM)
   - **Storage:** 10GB SSD
   - **Location:** us-central1-c

2. **Student Service (MongoDB Atlas)**
   - **Cluster Tier:** M0 Sandbox (Free)
   - **Location:** us-central1

3. **Media Service (Google Cloud Storage)**
   - **Bucket Name:** eca-media-bucket
   - **Storage Class:** Standard

4. **Frontend Application**
   - **Framework:** React 18 with TypeScript
   - **Build Tool:** Vite
   - **UI Library:** Material-UI

## Deployment Strategy

### Benefits of Cloud Run
- **Serverless Architecture:** No infrastructure management.
- **Auto-scaling:** Automatically handles traffic spikes.
- **Cost-effective:** Pay-per-use pricing.

### Database Selection
- **Cloud SQL:** Ideal for structured relational data.
- **MongoDB Atlas:** Suitable for flexible document storage.

## Configuration Details

### Course Service (Cloud SQL)
```properties
spring.datasource.url=jdbc:mysql://google/eca_courses?cloudSqlInstance=project-id:us-central1:course-db-instance&socketFactory=com.google.cloud.sql.mysql.SocketFactory&useSSL=false
spring.datasource.username=<your-mysql-username>
spring.datasource.password=<your-mysql-password>
```

### Student Service (MongoDB Atlas)
```properties
spring.data.mongodb.uri=mongodb+srv://<your-mongodb-username>:<your-mongodb-password>@<your-cluster-name>.mongodb.net/eca?appName=ECAStudentCluster
```

### Media Service (Cloud Storage)
```properties
spring.cloud.gcp.storage.bucket-name=eca-media-bucket
spring.cloud.gcp.credentials.location=/path/to/your/service-account-key.json
```

## Deployment Process

### Method 1: Google Cloud Console
1. **Enable APIs**: Cloud SQL Admin API, Cloud Storage API, Cloud Run Admin API.
2. **Create Cloud SQL Instance**: Configure MySQL instance.
3. **Create Cloud Storage Bucket**: Set up bucket for media storage.
4. **Create Service Account**: Grant necessary permissions.
5. **Deploy Services**: Use Cloud Run for deploying each service.

### Method 2: Command Line Interface (CLI)
1. **Authenticate and Set Up Project**: Use `gcloud` commands.
2. **Enable APIs**: Run a single command to enable all required APIs.
3. **Create Resources**: Use CLI commands to create SQL instance, storage bucket, and service account.
4. **Deploy Services**: Deploy each service using `gcloud run deploy`.

## Debugging and Cost Considerations
- Use `gcloud` commands to check deployment status and logs.
- Monitor costs associated with Cloud SQL, MongoDB Atlas, and Cloud Run.

## Conclusion
This project demonstrates a scalable, secure deployment of a microservices application on GCP, integrating various storage solutions and showcasing modern cloud practices.
