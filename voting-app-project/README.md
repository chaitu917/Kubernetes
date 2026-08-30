# Kubernetes Voting Application

## Project Overview

This project is a distributed voting application deployed and managed using Kubernetes.

The application allows customers/users to cast their votes through a Python-based voting application. Once a vote is submitted, the voting information is temporarily stored in an in-memory Redis database.

A .NET-based Worker application retrieves the voting data from Redis, processes the information, and stores the results permanently in a PostgreSQL database.

The processed voting results can then be viewed through a Node.js-based Result application.

## Application Architecture

The application consists of the following components:

1. **Voting Application - Python**
   - Provides the interface for customers/users to cast their votes.
   - Receives and publishes voting information to Redis.

2. **Redis - In-Memory Database**
   - Temporarily stores voting data.
   - Acts as the intermediate data store between the Voting application and Worker application.

3. **Worker Application - .NET**
   - Retrieves voting data from Redis.
   - Processes and filters the voting information.
   - Stores the processed data permanently in PostgreSQL.

4. **PostgreSQL - Persistent Database**
   - Permanently stores the processed voting data.
   - Provides reliable data persistence for the application.

5. **Result Application - Node.js**
   - Retrieves the processed voting results from PostgreSQL.
   - Provides an interface for users to view the voting results.

## Data Flow

The overall application flow is:

User
  ↓
Python Voting Application
  ↓
Redis (Temporary Storage)
  ↓
.NET Worker Application
  ↓
PostgreSQL (Permanent Storage)
  ↓
Node.js Result Application
  ↓
Voting Results

## Kubernetes Deployment

All application components are deployed as Kubernetes resources.

The project includes:

- Kubernetes Deployments
- Kubernetes Services
- Kubernetes Secrets
- Redis
- PostgreSQL
- Voting Application
- Worker Application
- Result Application

Kubernetes is used to manage application deployment, container orchestration, service communication, and scaling.

## Objective

The main objective of this project is to demonstrate how a multi-component application can be containerized and deployed using Kubernetes, with separate services communicating with each other through Kubernetes networking.
