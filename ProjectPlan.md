Overview: 
Our project looks at traffic crashes in Chicago and whether congestion, speeding, and road problems help explain where crashes happen and how bad they are. We will use four datasets from the City of Chicago Data Portal: Traffic Crashes, Historical Congestion Estimates, Speed Camera Violations, and 311 Service Requests. Each dataset has dates and locations, so we can match records by community area and month.
We will load the data with Python, clean the data and combine the four datasets to use for analysis. We hope to uncover any patterns or correlations by implementing data science techniques. In the end, we hope to show which parts of Chicago would benefit most from specific traffic safety improvement measures.

Team
Ariston Liu (Project direction and questions): Sets the project's goals and research question.
Brady Johnson (Dataset research): Finds, describes, and downloads the datasets and checks their licenses.
Sophia Kostov (Integration and constraints): Plans how to combine and clean the datasets and lists the project's limitations.
Anvith Mulpuri (Timeline and workflow): Builds the project timeline and the automated workflow that runs our scripts.


Research or Business Question: Across Chicago's community areas from 2019 to 2023, how are traffic congestion, speeding violations, and resident reported infrastructure problems associated with how often traffic crashes happen and how severe they are, and which areas should the city prioritize for traffic safety funding based on these factors?

Constraints: Our datasets are recorded in different geographic and time formats, so we will need to adjust the format so that we can aggregate the data to a common unit. The datasets also have coverage limits. Speed cameras only record violations where the cameras are actually placed, congestion data isn’t available for every street, minor crashes often go unreported, and 311 data relies on people actually reporting infrastructure problems. This means that our findings may favor areas that report more or are monitored more. The datasets also cover different time periods. We plan to limit our analysis to 2019-2023, when all datasets overlap. We can also only identify associations between variables but cannot prove causation.

Gaps: We need to find a way to reformat the geographic and time units within the datasets so that we can aggregate the data. If we cannot solve this issue, we may substitute datasets or revise our question. We also are considering adding population or traffic volume data so we can compare crash rates rather than raw counts. We also need to define how we will measure the severity of a crash and how to weigh factors when ranking areas for funding priority. 
