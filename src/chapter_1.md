# Chapter 1: Define and prepare the development environment

## Certification Objectives covered

- Select development environment
May include but is not limited to: Assess the deployment environment constraints, analyze and recommend tools that meet system requirements, select the development environment

- Set up development environment
 May include but is not limited to: Create an Azure data science environment, configure data science work environments
 [Azure Data Science Virtual Machines](https://azure.microsoft.com/en-us/services/virtual-machines/data-science-virtual-machines )

- Quantify the business problem
May include but is not limited to: Define technical success metrics, quantify risks

# A word of caution

At first glance, this certification objectives look out of order.
Why? because it makes more sense to quantify the business problem first, and then choose the tools (aka. development environment) that you will use for tacking the problem

# Quantify the Business Problem

A good start is taking a look at the [CRISP-DM](https://en.wikipedia.org/wiki/Cross-industry_standard_process_for_data_mining) methodology.
CRISP-DM starts with a "Understand the business problem" phase.
There is some stuff to take into account: 
- What kind of problem we want to solve?
- What's the current status? (the prior) Maybe this problem happens 1% of the time.
- What's the impact on the business? Try to put a money amount on the event. For instance, that 1% event might cost $1000s to the company.

# Select the Development Environment

## Microsoft service catalog for Data Science

Azure is a *huge* platform. Just take a look a the data and analytics-related services:

![Products in Azure console](images/Azure-Data-Analytics-Services.png)

Given this plethora of services... what can you do to get choose what suits best?

Microsoft has listed this services related to Machine Learning:

## Cloud-based options

The following options are available for machine learning in the Azure cloud.

| Cloud Option | Description | Use case 
|:-------------|:------------|:------------
| Azure Machine Learning service |	Managed cloud service for ML 	| Train, deploy, and manage models in Azure using Python and CLI 
| Azure Machine Learning Studio  |	Drag–and–drop visual interface for ML| 	Build, experiment, and deploy models using preconfigured algorithms (Python and R) 
| Azure Databricks |	Spark-based analytics platform  |	Build and deploy models and data workflows |
| Azure Cognitive Services |	Azure services with pre-built AI and ML models | Easily add intelligent features to your apps
| Azure Data Science Virtual Machine |	Virtual machine with pre-installed data science tools | 	Develop ML solutions in a pre-configured environment 

## On-premises options

The following options are available for machine learning on-premises.
On-premises servers can also run in a virtual machine in the cloud; but don't count on that. Sometimes you *need* to use on-prem services for compliance and/or regulatory reasons.

| On-premises option |	Description | Use case
|:-------------------|:------------|:-----------------
|SQL Server Machine Learning Services | Analytics engine embedded in SQL | Build and deploy models inside SQL Server
|[Microsoft Machine Learning Server](https://docs.microsoft.com/en-us/machine-learning-server/what-is-machine-learning-server) | Standalone enterprise server for predictive analysis | Build and deploy models with R and Python

## Development tools

Microsoft lists this as development tools for machine learning:
| Tool | Description | Use case 
|:-----|:------------|:-----------
| ML.NET 	| Open-source, cross-platform ML SDK | Develop ML solutions for .NET applications
| Windows ML | Windows 10 ML platform |	Evaluate trained models on a Windows 10 device (inference)

## What development environment to choose?

If you have an API available from Azure Cognitive Services (previously named Microsoft Cognitive Services, and Project Oxford), use it.
The time and effort required to have similar results are not worth trying when you can consume an API and start having results at the end of the day.

If you have a windows native application, or a C# one, Windows ML, or ML.NET might work for you.

SQL Server Machine Learning services are good when you want ot integrate ML into the database server. Why is it useful? apart from scoring or clustering from the database, on a BI environment you can use a ML model to predict the value of some facts that are not yet available in the database.

Microsoft Machine Learning Server (previously known as R Server) will allow you to serve models as webservices for your organization.  

# Setup development environment

** TODO: SETUP development environment **
