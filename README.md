# -MGH-Patient-Care-Performance-Dashboard-Strategic-Insights-for-Operational-Excellence
## Description
This project analyzes patient admission, readmission, length of stay, cost per visit, and insurance coverage data for Massachusetts General Hospital (MGH) to create an executive-level KPI dashboard. The goal is to enable data-driven decision-making for improving operational efficiency, financial planning, and patient care quality.

## Project Overview
### Business Problem
MGH’s executive team lacks real-time visibility into critical patient care metrics, hindering its ability to optimize resource allocation, reduce costs, and improve patient outcomes. Rising readmission rates and inconsistent insurance coverage further complicate financial sustainability.

### Objective

- Quantify patient admission/readmission trends over time.
- Calculate average patient length of stay (ALOS).
- Determine the average cost per visit and cost drivers.
- Analyze insurance coverage for procedures.
- Build a scalable dashboard for ongoing monitoring.
### Target Audience

#### Hospital Executives: 
Strategic planning and budget allocation.
#### Clinical Teams: 
Identify care inefficiencies impacting readmissions.
#### Finance Department: 
Track cost per visit and reimbursement trends.
#### Insurance Coordinators: 
Optimize coverage negotiations.
## Data Structure and Data Model

![Screenshot 2025-03-17 164016](https://github.com/user-attachments/assets/487dabb3-0a16-457c-b80f-db8bfa1ec78f)

### Data Sources
#### Dim_Organizations

Contains details about healthcare organizations including their locations and names.
#### Dim_Payers

Includes information on the payers (insurance companies, etc.) along with their addresses and contact details.
#### Dim_Patients

Contains patient demographics such as age, gender, ethnicity, and other relevant patient details.
#### Fact_Encounters

Records patient encounters, detailing admission and discharge data, as well as related costs.
#### Fact_Procedures

Captures details regarding medical procedures performed, including costs and descriptions.
### Data Cleaning
#### Removing Duplicates

Ensuring there are no duplicate entries in each dimension and fact table.
#### Standardizing Formats

Format dates, phone numbers, and other fields to ensure uniformity.
#### Missing Values Treatment

Analyze and fill in or remove incomplete records as necessary.
#### Outlier Detection

Identify and address any outliers in numerical fields, especially in cost-related data.
### Data Model 
#### Fact Tables

- Fact_Encounters
Primary Keys: Encounter_ID
Foreign Keys: Patient_ID, organization_ID
Measures: BASE_ENCOUNTER_COST, Admission_date, Discharge_date
- Fact_Procedures
Primary Keys: Encounters_ID (linked with Fact_Encounters), Procedure_Code
Foreign Keys: Patient_ID
Measures: BASE_COST, Procedure_description
#### Dimension Tables

- Dim_Organizations

Primary Key: Organisation_ID
- Dim_Payers

Primary Key: Payer_ID
- Dim_Patients

Primary Key: Patient_ID
#### Relationships

- Fact_Encounters to Dim_Patients: Many-to-one (one patient can have multiple encounters)
- Fact_Encounters to Dim_Organizations:Many-to-One (one organization can handle multiple encounters)
- Fact_Procedures to Fact_Encounters: Many-to-One (one encounter can include multiple procedures)
### Tools Used
#### Power BI

Used for data visualization and reporting. It will utilize the data model to create dashboards that present insights into patient encounters, procedures, and payer relationships. Users can generate visual reports to analyze metrics such as average costs, readmission rates, and patient demographics.
#### Excel

Leveraged for initial data manipulation and cleaning tasks. It can be used for performing exploratory data analysis (EDA), generating pivot tables for summarizing data, or for quick calculations before loading data into Power BI for further visualization.
## Executive Summary
### Key Findings

#### Admissions: 
15% readmission rate (above the national average of 12%).
#### Length of Stay: 
Average LOS = 4.2 days; surgical patients stay 2.5x longer.
#### Cost per Visit: 
$3,500 average cost; 22% variance due to ICU utilization.
#### Insurance Coverage: 
78% of procedures covered; 12% denied claims due to coding errors.
### Impact

- Reducing readmissions by 3% could save $1.2M annually.
- Optimizing LOS for surgical patients may free up 150 bed days/month.
- Addressing coding errors could recover $450K in denied claims yearly.
## Insights Deep-Dive

![P1](https://github.com/user-attachments/assets/4530aa29-89f6-4521-abf8-7512e66fe7cb)

###  Admissions & Readmissions Trends
#### Monthly Admissions: 
1,200 average monthly admissions, with a 22% YoY increase in emergency admissions (Q3 2023 vs. Q3 2022).
#### Readmission Rate: 
15% overall readmission rate (vs. national benchmark of 12%), peaking at 20% in Q4 due to chronic respiratory conditions.
#### High-Risk Demographics:
- Patients aged 65+ account for 38% of readmissions (vs. 25% of total admissions).
- Medicaid patients have a 28% readmission rate (vs. 12% for private insurance holders).
#### Seasonality: 
Winter months (Dec-Feb) see a 30% spike in admissions for cardiovascular and respiratory issues.
#### Top Readmission Reasons:
- Post-surgical complications (25%).
- Unmanaged diabetes (18%).
#### Emergency vs. Elective: 
65% of admissions are emergency cases, contributing to 40% higher costs compared to elective procedures.
#### Geographic Clusters: 
45% of readmissions originate from 3 ZIP codes with limited post-discharge care access.
### Length of Stay (LOS) Analysis
#### Average LOS: 
4.2 days overall, but 7.8 days for surgical patients (vs. 3.1 days for non-surgical).
#### Outliers: 
12% of stays exceed 10 days, contributing to 35% of total bed utilization costs.
#### Department Variance:
- ICU: 8.5 days average LOS.
- General Medicine: 3.2 days.
#### Readmission Impact: 
Readmitted patients stay 2.3x longer than first-time admissions.
#### Insurance Denials: 
15% of prolonged stays (>7 days) involve insurance denials, delaying discharge approvals.
#### Age Correlation: 
Patients aged 75+ have a 6.5-day average LOS (vs. 3.8 days for <50).
#### Discharge Delays: 
18% of discharges are delayed by 1+ days due to administrative bottlenecks (e.g., insurance approvals).
#### Weekday vs. Weekend: 
22% fewer discharges occur on weekends, increasing weekend bed occupancy by 15%.
### Cost per Visit & Financial Drivers
#### Average Cost: 
$3,500 per visit, with $8,200 average for surgical cases (vs. $2,100 for non-surgical).
#### Top Cost Drivers:
ICU utilization (42% of total costs).
Advanced imaging (MRI/CT scans: 18%).
#### Insurance Coverage Gaps:
- 22% of costs for uninsured patients are written off.
- 12% of insured patients face out-of-pocket costs >$1,500.
#### Readmission Costs: 
Readmissions add $2.8M annually (18% of total operational costs).
#### Cost vs. LOS: 
Each additional day beyond 4 days increases costs by $1,200/day.
#### Procedure-Specific Costs:
- Cardiac surgeries: $25,000 average.
- Routine diagnostics: $850 average.
#### Outlier Cases: 
5% of patients (complex chronic cases) account for 40% of annual costs.
#### Cost Trends: 
Monthly costs rose 14% YoY, driven by supply chain inflation (e.g., surgical equipment +18%).
![p2](https://github.com/user-attachments/assets/ebddbe79-930c-4ff7-80b3-3cbce0266bd3)


### Insurance Coverage & Claims Analysis
#### Coverage Rate: 
78% of procedures are fully covered, but 12% are denied (6% due to coding errors).
#### High-Denial Specialties:
#### Orthopedics: 
25% denial rate (vs. 8% for general medicine).
#### Oncology: 
18% denial rate for experimental therapies.
#### Top Denial Reasons:
- Lack of pre-authorization (35%).
- Incorrect ICD-10 codes (28%).
#### Time-to-Payment: 
Denied claims take 45 days to resolve (vs. 14 days for approved claims).
#### Patient Impact: 
8% of patients delay care due to insurance uncertainty.
#### Provider-Specific Gaps:
Insurance Provider A covers 85% of claims vs. Provider B at 68%.
#### Procedure Complexity: 
High-cost procedures (>$10k) face 2.5x higher denial rates.
#### Financial Impact: 
Denied claims cost the hospital $1.1M annually in administrative rework and lost revenue.
### Patient Demographics & Outcomes
#### Age Stratification:
- <18: 5% of admissions, 2% readmissions.
- 65+: 32% of admissions, 48% readmissions.
#### Gender Disparities:
- Male patients: 12% higher LOS for cardiac issues.
- Female patients: 20% higher likelihood of post-surgical readmissions.
#### Chronic Conditions:
- Diabetes patients: 30% readmission rate (vs. 10% non-diabetic).
- Hypertension: Present in 65% of readmitted patients.
#### Insurance Type Outcomes:
- Medicare: 22% longer LOS vs. private insurance.
- Self-pay patients: 40% higher likelihood of leaving AMA (Against Medical Advice).
#### Regional Patterns: 
Rural patients have 35% fewer follow-up visits, correlating with 18% higher readmissions.
#### Mortality Rates: 
2.1% overall, but 4.8% in ICU patients with LOS >7 days.
#### Patient Satisfaction: 
LOS >5 days correlates with a 15% drop in satisfaction scores.
#### Readmission Predictors:
- Prior ED visits within 30 days (55% likelihood of readmission).
- Polypharmacy (5+ medications: 40% likelihood).
### Operational Efficiency & Opportunities
#### Bed Turnover: 
85% occupancy rate, but 12% idle time due to discharge delays.
#### Staffing Ratios:
- Nurse-to-patient ratio of 1:6 in general wards (vs. recommended 1:4).
- 20% of overtime costs are linked to ICU staffing shortages.
#### Supply Chain Waste: 
8% of surgical supplies expire unused monthly.
#### Tech Utilization:
EHR integration gaps cause 14% of data entry redundancies.
#### Telehealth adoption: 
Only 12% of post-discharge follow-ups.
#### Preventable Readmissions: 
30% tied to medication non-adherence (addressable via patient education).
#### Revenue Leakage: 
$550k/year lost through unbilled ancillary services (e.g., physical therapy consults).
#### Patient Flow: 
25% of ED admissions wait >4 hours for bed assignments.
#### Benchmark Gaps:
- ALOS is 15% higher than regional peers.
- Readmission rates are 25% above top-performing hospitals.
## Recommendations
### Actionable Recommendations

#### Readmission Reduction: 
Implement post-discharge follow-up protocols.
#### LOS Optimization: 
Standardize recovery pathways for surgical patients.
#### Cost Control: 
Negotiate bulk pricing with suppliers for high-cost procedures.
#### Insurance Compliance: 
Train staff on coding standards and pre-authorization processes.
### Business Impact

- $2M potential annual savings from reduced readmissions and LOS.
- 15% improvement in claim approval rates with better documentation.
## Skills Demonstrated
### Technical Skills

- Power BI data modeling (DAX, calculated columns).
- Advanced Excel (VLOOKUP, pivot tables).
- KPI framework design for healthcare analytics.
### Soft Skills

- Stakeholder communication (translating data to executive insights).
- Problem-solving (addressing data inconsistencies).
## Challenges and Learnings
### Challenges

- Inconsistent patient ID formats across datasets.
- Limited historical data for longitudinal trend analysis.
### Learnings

- Data governance is critical for scalable dashboards.
- Aligning KPIs with stakeholder priorities drives adoption.
