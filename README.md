# Descrpitive Analysis Project
# Project Title: Implementing a Quality-Driven Data Analytics Solution on AWS for the City of Vancouver
# Objective
  The primary goal of this project is to conduct a descriptive analysis and design and implement a scalable and secure data analytics platform on AWS for the City of Vancouver that enables descriptive analytics on public datasets—specifically rental standards data—by establishing automated data ingestion, profiling, cleaning, and monitoring pipelines. The project aims to ensure data quality (completeness, uniqueness), enable governance through AWS CloudTrail, and deliver cost-effective, cloud-native solutions with detailed cost estimation and support planning.
  
# Data Analytical Platform for City Of Vancouver
<img width="702" alt="DAP" src="https://github.com/user-attachments/assets/ea047839-bbff-45dc-b13e-e3d552892386" />

# Dataset
The data set contains the rental property compliance data of the City of Vancouver, and currently these are unresolved by-law issues in licensed rental properties having 5+ units. It facilitates descriptive analysis in the process of establishing operators and neighborhoods that have many outstanding violations. Important columns are:
- BUSINESSOPERATOR: Rental property operator of the building which manages its name.
- DetailURL: Reference to detailed records of by-law concerns with the property.
- StreetNumber: The number of a street in which the property address is going to be set.
- Street: Name of the Street where the property under rent is to be.
- TOTALOUTSTANDING: Total number of unsolved by-law issues in the property.
- TotalUnits: Number of forms of residential dwelling units on the property.
- Geom: Geometry discipline standing in the capacity of property data (shape) of spatial (used in mapping).
- Geo Local Area: The geographic area (or neighbourhood) that the property is located in Vancouver.
- geo_point_2d - Latitude and longitude coordinates of property to explain geospatial mapping.

# Methodology
## Preparation and Collection of Data
This data was obtained using the City of Vancouver Open Data Portal and it shows information of rental buildings in the city that have 5+ units and have unresolved by-law concerns. Raw data was posted in Amazon s3. In AWS Glue DataBrew, the Null values in some essential columns (Geo Local Area, geo_point_2d, and Geom) were detected and eliminated. The information was further catalogued in AWS Glue data catalogue to analyse it further.
## Descriptive Statistics
- Total Properties: number of all rental records cleaned.
- Total Violations: a sum of all the outstanding by-law matters
- Average Violations per Property: used to determine the density of violation.
- Top Geo Areas: by Geo Local Area, to find out the areas with the biggest issues.
- Topmost Violation Operators: Listed property managers according to total outstanding 
## Observations and Conclusions
- Some of the neighborhoods are disproportion said to be the roots of these unresolved by-law issues
- There are also some property operators who are constantly present in the top bracket with a large number of outstanding violations.
- A lack of geo-coordinates was an issue of concern so it was the entry or system integration of the data at the source.
## Recommendations
- Concentrate resources devoted to enforcement or inspection for the most violation prone neighbourhoods and recurrent offending operators.
- Ensure quality of information being entered to prevent the absence of field data, geo-location related.
- It is worth considering making dashboards with the help of Amazon QuickSight or Power BI in order to monitor more in real-time.
- Automatically update the dataset and add a timestamp column, so that it is easier to track it and monitor its freshness.

# Tools and Technologies
## Amazon S3
The main source of data lake with structured hierarchies where data files (raw, cleaned, passed and failed) are kept.
<img width="944" alt="image" src="https://github.com/user-attachments/assets/f361ed69-450c-4bdf-93ab-17198bca3c67" />

## AWS Glue DataBrew
Profiling, cleaning, and detecting quality problems including missing values, duplicates are used. Facilitated validation and data transformation on a rule basis.
<img width="939" alt="image" src="https://github.com/user-attachments/assets/0ee995c2-28b6-4b65-be7b-ecba48404525" />

## AWS Glue Data Catalog
Assisted with a cataloging of the enriched dataset to be found and accessed into AWS services. Metadata was introduced to govern and trace.
<img width="959" alt="image" src="https://github.com/user-attachments/assets/594e3bce-2fa5-4b6e-a100-9c68b1144a4c" />

## Amazon Athena
Applied to perform SQL queries on the datasets stored on an S3 without having to migrate data to summarise, group, and obtain insights.
<img width="959" alt="image" src="https://github.com/user-attachments/assets/46b8ee4a-eb7f-451b-8151-dd3307404c9f" />

## AWS CloudWatch
It provided alerting mechanism and monitored stored usage on the S3 and other AWS services utilized on its platform.
<img width="953" alt="image" src="https://github.com/user-attachments/assets/dbfca011-070d-4d5a-aef5-59b96ce55b0f" />

## AWS CloudTrail
Monitoring usage of users and service activities within the platform to enable security, compliance, and audit needs.
<img width="953" alt="image" src="https://github.com/user-attachments/assets/9cb76ad9-ef19-4fcc-a88d-4e911d476192" />

## AWS Calculator
To approximate pricing of using the data analytics platform per month depending on S3, Glue, Athena services usage.

# Deliverables
## Data Analytics Platform in the Cloud
An AWS environment with a complete data analytics platform stored (S3), processed (Glue DataBrew), queried (Athena), monitored (CloudWatch), and governed (CloudTrail).
## Made clean dataset as well as enriched dataset.
The basic by-law violations on rentals dataset went through the process of cleaning by dropping missing fields of critical location, as well as validating and ensuring uniqueness, and also enriching.
## Descriptive Statistics Analysis
The information can be summarized with the use of the SQL queries of the number of violations by geographic area and allow focused decision-making.
## AWS cost estimation report
Storage, processing and analysing services costs by monthly cost projection created with the help of AWS Pricing Calculator.
## Attachment of Monitoring and Security
CloudTrail and CloudWatch were setup so as to monitor platform activities as well as performance and access in a way that ensured traceable and secure operations.
## Documenting and screenshots
An elaborate report encompassing every step (data ingestion, quality checks, etc.), the reason or cause/impact, tool, and screenshot illustration of the implementation.

# Findings
## Neighborhoods with Highest Violations:
According to the data summarisation from the SQL query, Downtown, Mount Pleasant, and West End showed that they were the areas that need the most attention by the department as the number of by-law violations in these areas was the highest. The total outstanding violations suggest that the aforementioned districts would be the best places for more specific operations or publicity.

<img width="516" alt="image" src="https://github.com/user-attachments/assets/5ebb77de-6eb5-4353-9afa-e493edc6e4c7" />

## Top Offending Property Operators:
Certain property operators consistently appear across multiple high-violation properties, suggesting potential issues in maintenance practices or compliance awareness.
## Uneven Distribution of Violations:
Violation counts vary significantly across geo-local areas, highlighting the need for area-specific policies or inspections rather than a city-wide uniform approach.
## Data Completeness Impact:
Missing values in location-based fields (e.g., Geo Local Area, Geo Point ID) initially affected the accuracy of geographic insights. After removing incomplete rows, the remaining data allowed more reliable neighborhood-level analysis.
# Suggestions
Based on the analysis, it is recommended that the City of Vancouver prioritize enforcement in high-violation areas such as Downtown, Mount Pleasant, and West End. Property operators with repeated unresolved violations should be engaged through targeted outreach or stricter penalties to improve compliance. Regular automated data quality checks should be implemented to ensure data completeness and accuracy, and dashboard tools like Amazon QuickSight or Power BI could be adopted for 
better visualization and decision-making. Standardizing data collection practices, especially ensuring fields like geo-local area are consistently populated, will enhance analysis reliability. Lastly, establishing strong data governance through AWS tools such as CloudTrail and IAM will ensure secure, transparent, and accountable management of the city’s rental standards data.

# AWS Deployment and Service Models
## Case Study #1: Traditional Computing Model vs Cloud Computing Model 
![image](https://github.com/user-attachments/assets/37e12325-ee87-45c0-affd-49145336aaf4)
The traditional model gives the City of Vancouver full ownership, control, and responsibility over the infrastructure, access, and privacy of its data. The cloud model provides scalability and remote accessibility, but involves shared responsibilities, especially around privacy and data access. By moving to the cloud, CoV gets operational benefits (like flexibility and performance), but must ensure proper agreements and safeguards with AWS to manage data privacy and compliance.
## Case Study #2: Cloud Deployment Models
<img width="707" alt="Case study 2-1" src="https://github.com/user-attachments/assets/3d4fbf61-762d-4184-942d-f675307895ce" />
<img width="364" alt="Case study 2-2" src="https://github.com/user-attachments/assets/2e622e13-6263-42d9-b68b-08946ee02266" />
<img width="591" alt="Case study results" src="https://github.com/user-attachments/assets/ac886135-4780-4f28-985d-ab9756a457cd" />

The case study had four cloud deployment models—Private Cloud, Public Cloud, Hybrid Cloud, and Multi-Cloud—used by the City of Vancouver (CoV) to manage the Rental Standards dataset. In the Private Cloud model, the dataset is hosted in CoV's own data center in Vancouver, ensuring full control over access and privacy. The Public Cloud model uses AWS infrastructure in Virginia, where CoV and AWS teams share access and privacy responsibilities, offering scalability but requiring careful configuration. The Hybrid Cloud model combines both private and public environments, allowing sensitive data to remain on-premise while utilizing cloud resources for flexibility, with privacy depending on the secure integration of both platforms. Lastly, the Multi-Cloud model leverages both AWS and Azure data centers, enabling CoV to distribute workloads across providers, which enhances redundancy and avoids vendor lock-in, though it demands more complex coordination and security management.
## Case Study #3: Cloud Service Models
<img width="794" alt="Cast study 3" src="https://github.com/user-attachments/assets/8312449c-ab8f-43f0-bb60-538601e1cd97" />
<img width="578" alt="Case study 3 result" src="https://github.com/user-attachments/assets/77295e66-d8b9-45ea-a6f7-d80e55daaecc" />

The case study 3 explains the three cloud service models—Infrastructure as a Service (IaaS), Platform as a Service (PaaS), and Software as a Service (SaaS)—as applied to the City of Vancouver's (CoV) Rental Standards dataset hosted on AWS in the Virginia region. In the IaaS model, CoV manages the virtual machines (EC2), storage (EBS), and network interfaces (NIC), with full control over the infrastructure and privacy, while AWS provides the underlying hardware. In PaaS, AWS additionally manages the platform (runtime, middleware), reducing CoV’s operational responsibility. Access is broader, and both CoV and AWS share responsibility for security. In the SaaS model, AWS controls almost everything, including the software layer. CoV only interacts with the application, while AWS manages the entire infrastructure and platform, and controls most of the data privacy. As service abstraction increases from IaaS to SaaS, CoV’s operational burden decreases, but so does its control over the environment and data privacy.
# AWS Cost Analysis 
## Case Study #4: Total Cost Of Ownership - Delaware North
![image](https://github.com/user-attachments/assets/b6fc6f60-99cb-47e4-a5bc-d71613cf6ed9)

This case study highlights how Delaware North, a large global company with over 200 locations and 500 million customers, reduced its total cost of ownership by moving to AWS. The company faced challenges in meeting rapid demand and upgrading outdated equipment. They needed a scalable and cost-effective solution to handle all workloads, improve efficiency, and ensure a good return on investment. By migrating their on-premise data centers and applications to AWS, they eliminated 205 physical servers (almost 90%) and adopted 3-year Amazon EC2 reserved instances. This shift allowed them to use resources more effectively, with enhanced security and performance, launch services faster (even within a day), and operate more efficiently and cost-effectively while staying online 24/7.
## Case Study #5: AWS Pricing Calculator
This case study helps me to calculate teh cost estimates for using different AWS services as part of a data analytics project for the City of Vancouver:
### Data Storage (Amazon S3 and AWS Glue Data Catalog):
Monthly cost: ~$3.14 USD,Annual cost: ~$37.31 USD
This includes storing standard-size objects and managing metadata about data sources. It's very affordable and scales well for small to moderate use.
![image](https://github.com/user-attachments/assets/40de4186-2a62-4350-8bf3-d9f650f6b630)  

### Data Profiling and Cleaning (AWS Glue DataBrew):
Monthly cost: ~$3.41 USD
Annual cost: ~$40.92 USD
This covers the cost of running interactive cleaning jobs using DataBrew. It’s used to prepare data by removing errors and standardizing it before analysis.
![image](https://github.com/user-attachments/assets/3bf7802f-7eae-4451-9647-1d4c9ea42c46)

### Data Analysis (Amazon Athena):
Monthly cost: $0.01 USD, Annual cost: $0.12 USD
Athena charges based on the amount of data scanned per query (here, ~1GB per month). This is ideal for low-cost, serverless querying.
## Case Study #6: Support Plan
![image](https://github.com/user-attachments/assets/ca9bbc77-089b-4864-996f-5b3a1768340d)

This case study recommends the Business Support Plan for the Data Analyst team because their work depends on reliable, fast, and secure access to analytics tools and data. Business Support provides quick access to AWS engineers and faster response times, helping maintain performance and ensure smooth decision-making processes.
# AWS Global infrastructure 
## Case Study #7: AWS Global Infrastruture
<img width="724" alt="image" src="https://github.com/user-attachments/assets/9086f57a-67a2-4ccc-8529-9f471e9dc1a9" />
<img width="517" alt="image" src="https://github.com/user-attachments/assets/3dabf526-f080-486b-a352-91cc9e2ff18c" />

I understood that AWS provides different layers of infrastructure to balance performance and data security. The Regional Edge Cache stores public data close to users for fast access, but has low privacy since it's read-only and publicly available. The Edge Location allows clients to both read and write data and is managed by AWS, offering moderate privacy. Finally, the Region layer (like AWS data centers in Virginia and Oregon) is where the full dataset is securely stored and managed by the City of Vancouver team with full control and high privacy.
The results are like
- Data stored in edge caches improves speed but offers less control.
- Edge locations allow more interaction but share responsibility with AWS.
- Regions provide the highest level of control and privacy, suitable for sensitive datasets.
- This setup helps ensure faster access for users while maintaining strong security for critical data.
# AWS IAM 
## Case Study #8: Who is responsible
<img width="762" alt="image" src="https://github.com/user-attachments/assets/0ccbfc32-c38e-4700-824d-2f460ed4359d" />

This diagram explains the shared responsibility model between the City of Vancouver (CoV) and AWS when using Amazon EC2 (Elastic Compute Cloud). CoV is responsible for everything inside the virtual server: configuring, securing, and managing the EC2 instance, deploying runtime environments (platform), installing and updating applications (software), and handling the dataset (creating, storing, and securing data). On the other hand, AWS is responsible for the infrastructure layer: ensuring the EC2 service is running, maintaining platform support, and securing the physical hardware and storage.
The result of this case study are CoV has full control and responsibility over what runs inside the server, while AWS ensures the underlying infrastructure is reliable and secure. This model allows CoV to retain flexibility while AWS guarantees uptime and hardware stability.
# AWS VPC
## Case Study #10: Build your VPC: Lab 2
<img width="583" alt="image" src="https://github.com/user-attachments/assets/54a04e89-d528-44d2-9013-af0013f3cc43" />

I completed and experienced Lab 1 which is an Introduction to AWS IAM as part of my AWS Academy training. Through this lab, I gained hands-on experience in managing permissions using IAM roles, users, and policies. It helped me understand how to control secure access to AWS services. I submitted the lab and i have some idea reflecting my understanding of the core IAM concepts. This practical exercise strengthened my confidence in applying IAM principles within real AWS environments.
# AWS Lambda 
## Case Study #11: Create an AWS Lambda function
<img width="635" alt="image" src="https://github.com/user-attachments/assets/7cf3f255-cf96-4419-8dc4-02f8d9f1d4a2" />

I practiced Lab 2: Build Your VPC and Launch a Web Server, where I learned how to create a Virtual Private Cloud (VPC), configure subnets, and launch a web server within AWS. This hands-on lab helped me understand key networking components like route tables, internet gateways, and security groups. It gave me practical experience in setting up a secure, isolated network environment—skills that are essential for deploying cloud applications and managing infrastructure in real-world scenarios.
# AWS EBS
## 
