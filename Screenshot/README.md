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
When I migrated the application to Azure, I chose AppService migration. Azure App Service has a great free tier (F1) and several cheap tiers that can be used for development and testing purposes; however, those tiers have a very limited amount of available CPU and RAM. Furthermore, it can autoscale when the application executes a task like sending mail to 100 or 1000 attendees. Sometimes the application is broken, and the cost is expensive. The solution is to push the notification to the Services Bus and trigger the function app to send mail to attendees. Using PostgresDb in the cloud saves money and securing a database server. The architecture is more cost effective.