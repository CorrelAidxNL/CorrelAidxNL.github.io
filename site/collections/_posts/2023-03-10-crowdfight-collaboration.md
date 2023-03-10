---
date: 2023-03-10 12:00:00
title: Helping Crowdfight facilitate scientific collaborations
description: >-
  Rewarding collaboration with Crowdfight!
author: Mehrzad
tags:
  - project 
  - matching
  - data science
image: /images/facilitating-collaborations-header.png
---

*This blog post was written by Mary Newhauser, Martin Baldenhofer, and Mehrzad Karami.*

We all remember the early days of the Covid-19 pandemic. Lockdowns, border closures, homemade face masks, toilet paper hoarding, and even mail microwaving. Looking back, it’s incredible to consider how little we knew about the virus that would kill millions and cause historic global disruption for years to come. We simply did not have answers to the most basic of questions about the virus. How deadly is it? How easily does it spread? Do face masks work? At the beginning of the pandemic, doctors, researchers, and the general public were hungry for answers, and that’s where Crowdfight came in.

# What is Crowdfight?
[Crowdfight](https://crowdfight.org/) is a non-profit dedicated to [facilitating scientific collaborations](https://www.youtube.com/watch?v=gyfMg7n2mv4) — especially those that don’t emerge naturally — by finding the experts needed to complement research projects and documenting the credit due to every participant. The organization grew out of an initiative at the beginning of the pandemic to facilitate knowledge transfer of Covid-related topics between medical researchers worldwide.

Realizing the value of the system they created, Crowdfight decided to open up their platform to researchers seeking collaborations on all sorts of topics, not just Covid. Crowdfight works like this: Researchers seeking collaborators for a specific task submit a request to Crowdfight which is then sent out to a list of researchers with matching skill sets who previously signed up to volunteer their time.

# Crowdfight and CorrelAid
The primary problem with Crowdfight’s current matching process is its imprecision. Approximately 93% of all Crowdfight users who respond to a request report that they are a poor match for the given task. To avoid user disengagement, Crowdfight wants to incorporate machine learning into the matching process, which is where CorrelAid steps in.

In a six-month sprint, a team of data scientists worked alongside a team of data engineers set up an automated pipeline, running in Google Cloud that pre-processes and saves all incoming Crowdfight data to Google BigQuery, so that Crowdfight can build and implement a machine learning solution that better matches prospective volunteers to requests in the future.

# Data science
Before our collaboration, Crowdfight data was collected through forms filled out directly by Crowdfight participants and inserted into Google Sheets. All the data needed to be cleaned and standardized, while the requests data needed to be enriched by being joined with an additional Google Sheet in which Crowdfight volunteers had assigned both a general and specific academic subject category.

To assess the quality of their current matching system, Crowdfight asked volunteers to rate the relevance of each volunteer task that was emailed to them. These responses were similarly saved in Google Sheets. In order to build a training dataset for Crowdfight, we needed to match up all the data for individual requests with the available responses. We also joined the response data with information that Crowdfight volunteers disclose when they sign up, including research area of expertise, highest level of education achieved, and the amount of time per week they can devote to a volunteer project.

The culmination of our efforts resulted in the following deliverables:

- Comprehensive data preprocessing script that consumes request, response, and volunteer data and writes clean versions of the data as well as an ML-ready training dataset to BigQuery.
- Jupyter notebook for exploratory data analysis that provides an overview of the current (baseline) performance of Crowdfight in matching requests to appropriate users.
- Training dataset that can be used for feature engineering, generating text embeddings, and model building, in the future.

# Data engineering
In the data engineering part of the project, we focused on deploying and operating a cloud infrastructure. Our ultimate goal was to move all data and code to the cloud and avoid having data distributed across different devices and running code with dependencies on local machines. When selecting the components for the deployment and the operation process we were focusing on easy maintenance and low cost.

Our deployment process is triggered automatically when changes are made to the main branch of the code repository. A GitHub action builds a Docker container from the Python code, which is then published to *Google Artifact*, a service provided by Google Cloud Platform that manages and hosts software artifacts.

To run the code, we use *Google Workflow* to orchestrate the different runs of the containers. *Google Workflow* is a workflow automation tool which coordinates the execution of multiple tasks or services. The containers are run on *Cloud Run*, a fully managed serverless container platform on the Google Cloud Platform which automatically scales the container instances based on incoming requests. When a *Cloud Run* job is triggered, it retrieves the corresponding Docker container from *Google Artifact*, which was previously published during the deployment process.

The code running inside the container reads and writes data against *Google BigQuery*, a fully managed, serverless data warehouse on the Google Cloud Platform that allows the analysis and querying of large datasets using SQL-like syntax.

We chose to use fully managed services by Google to make it easier for Crowdfight to maintain and scale the process. All services use Google Cloud IAM for authentication, so there is no need to generate and manage separate secrets/passwords for each service, making the whole process easy to manage and secure.

# Project coordination
Crowdfight noted that it was a great experience to work alongside our talented data scientists and data engineers together with their team of scientists. Here are some of the takeaways, as seen from the perspective of project coordination and support:

- The drive and the sheer amount of enthusiasm from our volunteers was one of the driving forces to move this project forward, and deliver excellent results.
- The level of expertise was superb. The mixture of expert level volunteers with newcomers in this field created a great learning environment for everyone working and contributing to this project.
- The leadership skills, especially from the tech leads of the data science as well as the data engineering team made it possible to deliver the project and tackle the obstacles and challenges early on in a very constructive and effective way.

The team consisted of the following people:
- CorrelAid:
    - Phase 1: Mathis Lucka, Lada Rudnitckaia, Chiel Bakkeren, Julia Masloh, Mehrzad Karami
    - Phase 2: Mary Newhauser (Lead Data Science team), Martin Baldenhofer (Lead Data Engineering), Barnaby Rumbold, Daljit Singh, Jaime Raldua Veuthey, Julian Werner, Sam Chien, Mehrzad Karami
- Crowdfight: Alfonso Pérez Escudero, Francisco Romero Ferrero

# Conclusion
Overall, this was a highly enjoyable collaboration! We are proud to have been able to help an organization that does such excellent work as Crowdfight, and we are excited to see how they will develop in the future. If you know an organization that could benefit from our data science and data engineering volunteers, please do not hesitate to [reach out](https://correlaid.nl/getinvolved/).