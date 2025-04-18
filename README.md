# Hospital Operations & Patient Outcomes Analysis

## Table of Contents
- [Project Background](#project-background)
- [Executive Summary](#executive-summary)
- [Dashboard](#dashboard)
- [Objectives](#objectives)
- [Tools and Technologies](#tools-and-technologies)
- [Dataset](#dataset)
- [Data Transformation](#data-transformation)
- [DAX Calculations](#dax-calculations)
- [Key Insights](#key-insights)
- [Recommendations](#recommendations)
- [Acknowledgements](#acknowledgements)

## Project Background

Hospitals are often challenged by the need to optimize resource utilization, manage patient flow, and provide quality care, especially in a context of limited resources. Effective management of admissions, patient stay durations, and resource allocation is critical to ensure operational efficiency and optimal patient outcomes. The Hospital Operations & Patient Outcomes Analysis project was initiated to address these challenges by providing a thorough analysis of hospital operations.

The goal was to identify inefficiencies in resource allocation, understand the factors affecting patient outcomes, and develop recommendations to enhance hospital efficiency. By analyzing patient admissions data, resource availability, and patient demographics, the project sought to provide actionable insights that could be leveraged to streamline processes, improve bed management, and allocate resources where they are needed the most.

## Executive Summary

The Hospital Operations & Patient Outcomes Analysis project focuses on optimizing hospital resource utilization and improving patient care outcomes. By analyzing hospital admissions, resource allocation, and length of stay, key inefficiencies were identified across wards and departments. The analysis revealed that wards such as Ward R were significantly more crowded, while others, like Ward P, had underutilized resources. Trauma cases were especially prevalent among patients aged 41-50, suggesting a need for enhanced preventive care programs.

Recommendations included reallocating resources from underutilized wards to high-demand areas, focusing on preventive care for high-risk age groups, and applying efficiency strategies from the best-performing wards to others. These actionable insights aimed to streamline hospital operations, enhance patient experiences, and optimize resource use.

## Dashboard

![Dashboard_Main](https://github.com/user-attachments/assets/527a85e3-0cee-4805-8fad-579f392a6aca)

## Objectives

- **Analyze Resource Utilization**: Understand how hospital resources, such as staff and beds, are being utilized across different wards to identify inefficiencies.
- **Identify Factors Impacting Patient Outcomes**: Determine the key factors that influence patient outcomes, including resource allocation, length of stay, and emergency preparedness.
- **Provide Actionable Insights for Improvement**: Generate insights into operational bottlenecks, underutilized resources, and potential areas for preventive measures.
- **Recommend Strategies to Improve Efficiency**: Develop recommendations to enhance hospital operations, reduce patient wait times, and improve overall patient care and satisfaction.

## Tools and Technologies

- **Excel Power Pivot**: For data preparation, transformation, and initial analysis.

## Dataset

The dataset used for this project is anonymized to protect patient privacy and does not contain any personally identifiable information (PII). The data includes:

![image](https://github.com/user-attachments/assets/4b0511f6-e37e-44f8-97a8-a8833a99dc81)

- Patient admissions by department and ward.
- Age groups and type of admission (emergency, trauma, urgent).
- Resource allocation: Number of available rooms and admissions.
- Length of stay by severity of illness.

## Data Transformation

- **Converted Columns to Text Format**: 
  - Changed the data type of the columns `case_id`, `hospital_code`, and `city_code_hospital` to text.
  - Changed the data type of the columns `patientid` and `bed grade` to text.

- **Replaced Age Range Values**: 
  - Replaced the value `"51-60"` with `"51-60 years"` in the age column to make the data more descriptive.

- **Split the 'Stay' Column into Two Parts**: 
  - Split the `Stay` column into two new columns: `Stay.1` (lower bound) and `Stay.2` (upper bound) based on the hyphen delimiter, preparing the data for further manipulation or calculation.

- **Calculated the Midpoint of Stay Ranges**: 
  - Created a new column to calculate the midpoint of the stay duration using the formula:
  ```excel
  =(Hospital_Data[Stay.1] + Hospital_Data[Stay.2]) / 2

## DAX Calculations

```dax
Total Admissions = COUNTROWS(Hospital_Data)
```
```dax
Emergency Patients = CALCULATE(COUNTROWS(Hospital_Data), Hospital_Data[Type of Admission] = "Emergency")
```
```dax
Trauma Patients = CALCULATE(COUNTROWS(Hospital_Data), Hospital_Data[Type of Admission] = "Trauma")
```
```dax
Urgent Patients = CALCULATE(COUNTROWS(Hospital_Data), Hospital_Data[Type of Admission] = "Urgent")
```
```dax
Average Stay Duration = AVERAGE(Hospital_Data[Average_Stay])
```

## Key Insights
Gynecology handles over 45,000 trauma and 40,000 emergency cases—consider allocating more resources to this department to manage the high volume of critical cases.

![image](https://github.com/user-attachments/assets/9f157448-c83f-4791-b7f2-6cb2a9a5cb43)

Trauma cases peak at over 25,000 in the 41-50 age group, while emergency cases are also highest in the 41-50 age group with 16,875 admissions—focus on trauma prevention and emergency preparedness for these age groups (31-60).

![image](https://github.com/user-attachments/assets/cb3cb632-7562-4448-abc5-b47b0b7aa35b)

Patients with extreme trauma have the longest average stay at 41 days, while emergency and urgent cases average 38 days—consider process improvements to reduce stays for extreme trauma cases.

![image](https://github.com/user-attachments/assets/e10fc978-79d4-4709-a65d-bf8640dde82b)

Ward S has the longest average stay at 43 days, while Ward U has the shortest at 25 days—explore applying Ward U's efficiency strategies to reduce stay durations in Ward S.

![image](https://github.com/user-attachments/assets/79f003f8-f058-4423-80c5-e8d2b0b1862a)

Ward R has 90,538 admissions and 3 extra rooms, while Ward P has 3,376 admissions with the most extra rooms (5). 
Ward U shows the lowest admissions with 3 extra rooms—consider reallocating resources from Ward U to busier wards like R.

![image](https://github.com/user-attachments/assets/c046fcc4-ef7c-4847-96c0-3023c13a09fa)



## Recommendations
Optimize resource allocation: Reallocate resources from underutilized wards (e.g., Ward P) to high-demand wards (e.g., Ward R).

Focus on preventive care: Target trauma prevention programs for the 41-50 age group and improve emergency preparedness for the 51-60 age group.

Increase efficiency: Implement strategies from Ward U to reduce patient stay durations in high-demand wards like Ward S.

# Acknowledgements
This project was made possible by anonymized hospital data, with the aim of improving patient care and resource management.
