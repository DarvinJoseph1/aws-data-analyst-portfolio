
# Final AWS Portfolio Project Report – Darvin Joseph

## Descriptive Analysis

### Project Description
Descriptive Analysis of Employee Turnover Patterns

### Project Title
Understanding Employee Turnover Patterns at XYZ Retail

### Objective
The primary goal of this project is to conduct a descriptive analysis of customer purchase data at XYZ Retail. Through this analysis, we aim to summarize key characteristics of customer purchases, identify trends, and generate insights that can inform marketing strategies and inventory management.

### Dataset
The dataset includes structured HR exit and employee records from XYZ Corp (City of Vancouver HR Department) collected over the past 12–18 months, with the following key features:
- Employee ID: Unique identifier for each employee
- Department: Department the employee worked in (e.g., HR, Marketing, IT)
- Exit Date: Date of official departure
- Exit Type: Whether the exit was voluntary or involuntary
- Exit Reason: Categorized reason for leaving (e.g., better opportunity, retirement, conflict)
- Service Duration: Number of years/months served
- Gender: Gender identity of the employee
- Age Group: Categorized age range (e.g., 18–24, 25–34, 35–44)

### Methodology
1. **Data Collection and Preparation**:
   - Loaded employee exit datasets into Amazon S3 using a structured Datalake design.
   - Performed data cleaning using AWS DataBrew to fix invalid timestamps and missing fields.
   - Tagged and organized files by department and exit type.

2. **Descriptive Statistics**:
   - Calculated total exits and average tenure.
   - Counted exits per department/month and by type (voluntary/involuntary).
   - Analyzed gender and age distribution.

3. **Visualization**:
   - Created time series graphs of monthly exits.

4. **Employee Segmentation**:
   - Grouped by tenure: early (<1 year), mid-career (1–5 years), long-term (>5 years).
   - Compared exit reasons and voluntary/involuntary breakdowns.

5. **Insights and Findings**:
   - Peak exits in Q1 and Q4 due to fiscal cycle or performance reviews.
   - Highest turnover in HR and Marketing.
   - Voluntary exits due to lack of growth opportunities.

6. **Root Cause Analysis**:
   Conducted using a Fishbone diagram identifying:
   - Policy gaps
   - System/tool limitations
   - Process inconsistencies
   - Low morale
   - Stress and early exits

7. **Dataset Storage Architecture**:
   - AWS S3 bucket: `HR-raw-b`, with tagging and tiered storage (Standard, Glacier Deep Archive).
   - Region: `us-east-1` (Virginia).

8. **Recommendations**:
   - Create retention programs for <2 year employees.
   - Improve career paths in high-turnover departments.
   - Standardize exit interviews.
   - Use dashboards for real-time trends.

---

## Tools and Technologies

- **AWS Services**: S3, EC2, DataBrew, Glue, CloudWatch, Lambda, CloudTrail
- **Data Analysis**: AWS Athena
- **Visualization**: draw.io (Fishbone, architecture)
- **Documentation**: Word, PDF, tagged datasets in S3

---

## Deliverables

- AWS Datalake with raw, clean, curated datasets
- Cleaned and profiled dataset
- Root cause Fishbone diagram
- Summary report of methodology and insights
- Visualizations by department, tenure, reason
- Stakeholder presentation deck

---

## AWS Deployment and Service Models

We compared on-premises vs AWS cloud-based solutions for the capital planning dataset of the City of Vancouver.

### Cloud Deployment Models

- **Private Cloud**: Local servers at city data centers, fully controlled but limited access and higher overhead.
- **Public Cloud**: AWS S3 globally accessible, IAM-managed, scalable.
- **Hybrid Cloud**: Sensitive data internal; anonymized data in AWS S3 (Glue, Athena) for analysis.
- **Multi-Cloud**: AWS for ingestion; Azure for archiving and integration with Microsoft-based internal systems.

### AWS Service Models

- **IaaS**: EC2, EBS – full control, high responsibility
- **PaaS**: Glue, Athena – managed environment, reduced admin
- **SaaS**: Minimal configuration, end-user friendly, limited control

---

## AWS Cost Analysis

- TCO Case: Migrating 205 servers to AWS saved 90% of infra cost.
- AWS Pricing Calculator showed $13.58/year for S3 storage.
- Glue DataBrew helped profile and clean HR dataset.
- ETL jobs created in Glue Studio.
- Developer Support Plan chosen for troubleshooting and documentation.

---

## AWS Global Infrastructure

- Region: Virginia (us-east-1)
- IAM, KMS, CloudTrail used for governance
- Edge locations & CloudFront ideal for dashboards and open datasets
- Regional edge caches improve access speed

---

## AWS IAM (Module 4)

- User-1: S3-Support (read-only access to S3)
- User-2: EC2-Support (read-only EC2 access)
- User-3: EC2-Admin (can start/stop EC2)
- Follows principle of least privilege
- Tested real-time access limits

---

## AWS VPC (Module 5)

- Created public and private subnets across AZs
- Deployed EC2 in public subnet (inbound HTTP rule missing)
- Subnet routing and security groups used
- Mirrors DAP's layered network security

---

## AWS Lambda (Module 6)

- Built Lambda to auto-stop EC2 with CloudWatch trigger
- Used Python (Boto3)
- Use-case: automate Glue logs archiving, notify on S3 data update
- Supports DAP’s serverless automation needs

---

## AWS EBS (Module 7)

- Created, mounted, and snapshot an EBS volume
- EBS used for temporary high-performance ETL storage
- Snapshots used for rollback/versioning
- Supports recoverability across raw, clean, curated datasets

---

## Conclusion

The project successfully demonstrated secure, scalable, and cost-effective HR analytics using AWS. Every lab module and AWS service aligns with a real component of the City of Vancouver's DAP initiative—from S3 data lakes to IAM roles, Glue pipelines, and serverless operations with Lambda.

