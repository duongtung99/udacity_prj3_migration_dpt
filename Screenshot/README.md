# TechConf Registration Website

## Project Overview
The TechConf website allows attendees to register for an upcoming conference. Administrators can also view the list of attendees and notify all attendees via a personalized email message.

The application is currently working but the following pain points have triggered the need for migration to Azure:
 - The web application is not scalable to handle user load at peak
 - When the admin sends out notifications, it's currently taking a long time because it's looping through all attendees, resulting in some HTTP timeout exceptions
 - The current architecture is not cost-effective 

In this project, you are tasked to do the following:
- Migrate and deploy the pre-existing web app to an Azure App Service
- Migrate a PostgreSQL database backup to an Azure Postgres database instance
- Refactor the notification logic to an Azure Function via a service bus queue message

## Advantages and disadvantages
# Web App
 Advantages:   Cost-Effective
               Always up-to-date
               Free From Downloading Needs
               Runs Easy
Disadvantages: Internet Reliance
               Website Dependency
               Reduced Speed
               Restricted Functionality

## Monthly Cost Analysis
Complete a month cost analysis of each Azure resource to give an estimate total cost using the table below:

| Azure Resource   | Service Tier | Monthly Cost |
| ---------------- | ------------ | -------------- |
| Azure PostgreSQL |   Basic      |   $43.55       |
| Azure Service Bus|   Basic      |   $0.05        |
| Azure App Service|   Basic (B1) |   $13.14       |
| Azure Storage    |   Basic      |   $0.10        |

The app service includes the web app and the function app.

## Architecture Explanation
The azure web app was already built out, I only had to change the environment variables within config.py and refactor the notification flow within app.py. Everything else was already configured. The costs are reasonable, outside of the PostgreSQL database, which is by far the most expensive part of the architecture. Creating a service bus namespace to handle the notifications is a good idea, but if it could all be saved to a less expensive database that would be the most straightforward way to lower costs. 

Other than changing up the database, everthing else is available at a reasonable cost.