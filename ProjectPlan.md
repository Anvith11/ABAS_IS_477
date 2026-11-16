# Overview: 
Our project looks at traffic crashes in Chicago and whether speeding and road problems help explain where crashes happen and how bad they are. We will use three datasets from the City of Chicago Data Portal: Traffic Crashes, Speed Camera Violations, and 311 Service Requests, along with population estimates for each community area. Each dataset has dates and locations, so we can match records by community area and month. We will load the data with Python, clean the data and combine the datasets to use for analysis. To compare busy and quiet areas fairly, we will measure crashes, violations, and road problems per 10,000 residents instead of using raw counts. We hope to uncover any patterns or correlations by implementing data science techniques. In the end, we hope to show which parts of Chicago would benefit most from specific traffic safety improvement measures.

## Team
Ariston Liu (Project direction and questions): Sets the project's goals and research question.
Brady Johnson (Dataset research): Finds, describes, and downloads the datasets and checks their licenses.
Sophia Kostov (Integration and constraints): Plans how to combine and clean the datasets and lists the project's limitations.
Anvith Mulpuri (Timeline and workflow): Builds the project timeline and the automated workflow that runs our scripts.


## Research or Business Question: 
Across Chicago's community areas from 2019 to 2023, how are speeding violations and resident reported road infrastructure problems associated with how often traffic crashes happen and how severe they are, and which areas should the city prioritize for traffic safety funding based on these factors?

## Dataset Research
For this project, we initially found four datasets from the City of Chicago public records. These are accessible, easy to download, and easy to understand data sets. The common attribute amongst all dataset is location and date. After profiling the data, we removed the congestion dataset and added population estimates so we can calculate rates.

Crashes (https://data.cityofchicago.org/Transportation/Traffic-Crashes-Crashes/85ca-t3if/about_data): This dataset gives us the location, time, severity and cause of the crash. This is the backbone to our research.

Removed: Congestion (https://data.cityofchicago.org/Transportation/Chicago-Traffic-Tracker-Historical-Congestion-Esti/sxs8-h27x/about_data): This dataset was organized by stretches of street with a start street and an end street instead of single locations, which made it hard to match to community areas. It also only estimates congestion from CTA bus data on major streets. Because of this, we removed it from the project and from our research question.

Speed Camera Violations (https://data.cityofchicago.org/Transportation/Speed-Camera-Violations/hhkd-xvj4/data_preview): This dataset says the time, place, location, and speed of speed camera violations in Chicago. This will allow us to track common speeding to zones to see if speed is a factor in common crash areas.

311 Infrastructure Service Requests (https://data.cityofchicago.org/d/v6vf-nfxy): This data set shows location, date, and what type of requests were submitted for the roads of Chicago. This will allow us to see if low maintence zones have more crashes.

ACS 5 Year Data by Community Area (https://data.cityofchicago.org/d/t68z-cikk): This dataset gives population estimates for each of Chicago's 77 community areas from the American Community Survey 2019 to 2023 5 year estimates, which match our study period. We will use total population to turn our counts into rates per 10,000 residents.

## Integration: 
Integration of the datasets will be done using the Chicago community area and month as the common spatiotemporal unit between 2019 and 2023. The three event datasets will be cleaned individually with respect to date standardization, location, missing data, and other relevant attributes. Traffic crashes will be aggregated according to community area and month for crash counts and crash intensity. The speed camera violations will be aggregated on the basis of the month and linked to the respective community areas, while 311 service requests related to roads and infrastructure will be filtered out and similarly aggregated. The datasets will then be combined into one single integrated dataset using community area and month as the major linking fields. Population from the ACS dataset will be joined by community area, and each count will be divided by population and multiplied by 10,000 to get rates per 10,000 residents, so that areas with more people are not ranked higher just because of their size. In the process of integration, accuracy, completeness, timeliness, and consistency of the datasets will be checked. Similarly, a quality check will be performed post-integration to assess whether the datasets have been integrated properly and to find any records or locations which have poor data coverage. Each part of the process, namely data acquisition, quality check, data cleaning, data integration and analysis will be done by separate Python scripts; however, there will also be a run-all Python script which will make this project a reproducible workflow. All the Python scripts will be using relative paths and will document the required dependencies for them to run from a fresh checkout of the GitHub repository without having to make any manual modifications to it.

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
Our datasets are recorded in different geographic and time formats, so we will need to adjust the format so that we can aggregate the data to a common unit. The datasets also have coverage limits. Speed cameras only record violations where the cameras are actually placed, minor crashes often go unreported, and 311 data relies on people actually reporting infrastructure problems. This means that our findings may favor areas that report more or are monitored more. Population numbers are estimates from the American Community Survey and are given as one average for 2019 through 2023, so our rates will not reflect population changes from year to year. We also removed the congestion data, so we cannot measure how much traffic each area has. The datasets also cover different time periods. We plan to limit our analysis to 2019-2023, when all datasets overlap. We can also only identify associations between variables but cannot prove causation.
## Gaps: 
We need to find a way to reformat the geographic and time units within the datasets so that we can aggregate the data. If we cannot solve this issue, we may substitute datasets or revise our question. We have added population data so we can compare crash rates per 10,000 residents rather than raw counts. We also need to define how we will measure the severity of a crash and how to weigh factors when ranking areas for funding priority.
