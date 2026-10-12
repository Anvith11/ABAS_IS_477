# Overview: 
Our project looks at traffic crashes in Chicago and whether congestion, speeding, and road problems help explain where crashes happen and how bad they are. We will use four datasets from the City of Chicago Data Portal: Traffic Crashes, Historical Congestion Estimates, Speed Camera Violations, and 311 Service Requests. Each dataset has dates and locations, so we can match records by community area and month.
We will load the data with Python, clean the data and combine the four datasets to use for analysis. We hope to uncover any patterns or correlations by implementing data science techniques. In the end, we hope to show which parts of Chicago would benefit most from specific traffic safety improvement measures.

## Team
Ariston Liu (Project direction and questions): Sets the project's goals and research question.
Brady Johnson (Dataset research): Finds, describes, and downloads the datasets and checks their licenses.
Sophia Kostov (Integration and constraints): Plans how to combine and clean the datasets and lists the project's limitations.
Anvith Mulpuri (Timeline and workflow): Builds the project timeline and the automated workflow that runs our scripts.


## Research or Business Question: 
Across Chicago's community areas from 2019 to 2023, how are traffic congestion, speeding violations, and resident reported infrastructure problems associated with how often traffic crashes happen and how severe they are, and which areas should the city prioritize for traffic safety funding based on these factors?

## Dataset Research
For this project, we initially found four datasets from the City of Chicago public records. These are accessible, easy to download, and easy to understand data sets. The common attribute amongst all dataset is location and date.

Crashes (https://data.cityofchicago.org/Transportation/Traffic-Crashes-Crashes/85ca-t3if/about_data): This dataset gives us the location, time, severity and cause of the crash. This is the backbone to our research.

Congestion (https://data.cityofchicago.org/Transportation/Chicago-Traffic-Tracker-Historical-Congestion-Esti/sxs8-h27x/about_data) This dataset tracks how busy certain locations are in Chicago. This will allow us to figure out volume calculations and determine if crashes just occur where people drive more frequently.

Speed Camera Violations (https://data.cityofchicago.org/Transportation/Speed-Camera-Violations/hhkd-xvj4/data_preview): This dataset says the time, place, location, and speed of speed camera violations in Chicago. This will allow us to track common speeding to zones to see if speed is a factor in common crash areas.

311 Infrastructure Service Requests (https://data.cityofchicago.org/d/v6vf-nfxy): This data set shows location, date, and what type of requests were submitted for the roads of Chicago. This will allow us to see if low maintence zones have more crashes.


## Integration: 
Integration of the four datasets will be done using the Chicago community area and month as the common spatiotemporal unit between 2019 and 2023. The four datasets will be cleaned individually with respect to date standardization, location, missing data, and other relevant attributes. Traffic crashes will be aggregated according to community area and month for crash counts and crash intensity, while traffic congestion data will be aggregated accordingly. The speed camera violations will be aggregated on the basis of the month and linked to the respective community areas, while 311 service requests related to roads and infrastructure will be filtered out and similarly aggregated. The four datasets will then be combined into one single integrated dataset using community area and month as the major linking fields. In the process of integration, accuracy, completeness, timeliness, and consistency of the four datasets will be checked. Similarly, a quality check will be performed post-integration to assess whether the datasets have been integrated properly and to find any records or locations which have poor data coverage. Each part of the process, namely data acquisition, quality check, data cleaning, data integration and analysis will be done by separate Python scripts; however, there will also be a run-all Python script which will make this project a reproducible workflow. All the Python scripts will be using relative paths and will document the required dependencies for them to run from a fresh checkout of the GitHub repository without having to make any manual modifications to it.

## Timeline

| Time Period | Task | Description | Responsible Member(s) |
|---|---|---|---|
| Oct. 12 | Finalize Project Plan | Complete the project plan, review all sections, and create the project-plan GitHub release. | All members |
| Oct. 13–18 | Data Acquisition | Download the four datasets, document sources and licenses, verify data integrity, and organize the repository. | Brady |
| Oct. 19–25 | Data Profiling | Examine columns, data types, date ranges, geographic fields, missing values, duplicates, and other potential data quality issues. | Brady & Sophia |
| Oct. 26–Nov. 1 | Pre-Integration Quality Assessment | Evaluate accuracy, completeness, timeliness, and consistency for each dataset and document issues that need cleaning. | Sophia |
| Nov. 2–8 | Data Cleaning | Standardize dates and locations, address missing or inconsistent values, filter relevant 311 requests, and prepare the datasets for integration. | Sophia |
| Nov. 9–15 | Data Integration | Aggregate the four datasets by community area and month and join them into a single dataset covering 2019–2023. | Sophia & Anvith |
| Nov. 16–19 | Interim Status Report | Document progress, challenges, changes to the project plan, individual contributions, and the updated timeline. | All members |
| Nov. 20–24 | Post-Integration Quality Assessment | Evaluate the accuracy, completeness, timeliness, and consistency of the integrated dataset and verify that integration was successful. | Sophia & Anvith |
| Nov. 25–29 | Analysis and Visualization | Analyze relationships between crashes, congestion, speeding violations, and infrastructure problems and create visualizations of important patterns. | Ariston & Anvith |
| Nov. 30–Dec. 3 | Workflow and Documentation | Connect the separate scripts with a run-all workflow and complete dependencies, metadata, data documentation, and reproduction instructions. | Anvith |
| Dec. 4–5 | Final Report | Complete the README with the required project findings, data profiles, quality assessment, cleaning methods, challenges, future work, and references. | All members |
| Dec. 6 | Reproducibility Testing | Clone the repository into a clean environment and test the complete workflow from data acquisition through analysis. | All members |
| Dec. 7 | Final Submission | Make final corrections, create the final-project GitHub tag and release, and submit the release URL to Canvas. | All members |

## Constraints: 
Our datasets are recorded in different geographic and time formats, so we will need to adjust the format so that we can aggregate the data to a common unit. The datasets also have coverage limits. Speed cameras only record violations where the cameras are actually placed, congestion data isn’t available for every street, minor crashes often go unreported, and 311 data relies on people actually reporting infrastructure problems. This means that our findings may favor areas that report more or are monitored more. The datasets also cover different time periods. We plan to limit our analysis to 2019-2023, when all datasets overlap. We can also only identify associations between variables but cannot prove causation.

## Gaps: 
We need to find a way to reformat the geographic and time units within the datasets so that we can aggregate the data. If we cannot solve this issue, we may substitute datasets or revise our question. We also are considering adding population or traffic volume data so we can compare crash rates rather than raw counts. We also need to define how we will measure the severity of a crash and how to weigh factors when ranking areas for funding priority. 
