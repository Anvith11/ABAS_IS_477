# Milestone 3: Interim Status Report

**Project:** Chicago Traffic Safety Analysis  
**Status date:** November 15, 2026

## Project Overview

Our project examines how recorded speed-camera violations and resident-reported road infrastructure problems are associated with reported crash frequency and severity across Chicago community areas from 2019 through 2023. We plan to compare records by community area and calendar month. The results can help identify areas for further traffic safety review, but they will not establish what caused individual crashes.

## Data Profiling
Crashes - Lots of data we can use. Includes speed limits, curve, type of crash. Address is already separated by number, direction, and name, so integration should be easier.  
Congestion - Was organized in chunks of streets. It had a start street and an ending street, so it would be hard to integrate. We made the decision to exclude this data set. Also, only gives bus count to help estimate congestion time, we do not have historical Chicago data to help us estimate.  
Speed Camera - Has location not separated out, but does include number, direction, and name. Has coordinates and number of violations additionally. This will be a very crucial dataset for us because we will be able to tell which areas are high speed.  
311 Service Requests - This dataset was originally 14,000,000 rows. This is because it included all requests from aviation noise complaints to leaf removals, and waste complaints. I filtered it down to only include requests that involved CDOT - Department of Transportation. These requests involve pothole notices, sign repairs, road repair requests, etc. Has street address with number, direction, and name, but it is not separated out.

## Task Update

Pre-Integration Quality Assessment

We are assessing accuracy, completeness, timeliness, and consistency for each dataset. Initial results from profiling are as follows. Coordinates are usable in the large majority of crashes and in 311 and date and location formats differ across datasets.

Data Cleaning

We plan to standardize dates to year-month, drop or flag crashes and 311 requests with missing or (0,0) coordinates, remove or flag 311 rows marked DUPLICATE, and filter 311 to road-related request types (potholes, street and alley lights, traffic signals, road signs, pavement and sewer cave-ins).

**Data acquisition and documentation.** The [crash](data/traffic_crashes.csv), [speed-camera](data/speed_camera_violations.csv), and [311](data/service_requests.csv) files are tracked through [Git LFS](.gitattributes). We still need to verify that a fresh clone retrieves readable CSVs and finish documenting sources, licenses, and filters. The [revised project plan](ProjectPlan.md) identifies ACS population estimates as a reference input, but an extract and geographic matching method were not committed in the November 15 snapshot.

**Integration and analysis.** The quality assessment and cleaning files in [`script/`](script/) are placeholders. Once runnable scripts are available, we will assign community areas and aggregate each dataset separately before joining on area and month. Joining raw records first could multiply rows and inflate totals. No merged output or analysis was committed as of this update. After validating the merge, we will define the crash severity measure and create exploratory summaries and figures.

**Workflow and reproducibility.** The [workflow document and diagram](docs/workflow.md) describe the planned pipeline and expected outputs. The workflow still needs the population-matching step. The automated runner will connect the stage scripts after their inputs and outputs are agreed upon and tested.

## Updated Timeline

The original November 15 integration target was not met because cleaning and geographic assignment were still pending. Dates for unfinished work are proposed team targets.

| Task | Status as of November 15 | Completed or target |
|---|---|---|
| Finalize and revise the project plan | Original plan completed; congestion removed and population rates proposed. | Oct. 12; revised Nov. 15 |
| Acquire and document event data | Three inputs committed; verify retrieval and complete source documentation. | Nov. 18 |
| Profile data and assess pre-integration quality | Initial findings documented; add counts for invalid coordinates, duplicates, and date coverage. | Nov. 19 |
| Complete interim report | Draft committed; finish task updates and individual summaries, then publish `status-report`. | Nov. 19 |
| Clean event data | Rules drafted; implement and test them. | Nov. 21 |
| Integrate event data | Assign community areas, aggregate each source, and join by area and month. | Nov. 23 |
| Match population and validate the merge | Document ACS matching, check unique keys, reconcile totals, and report coverage gaps. | Nov. 24 |
| Analyze and visualize | Define severity, calculate supported rates, and create figures after validation. | Nov. 25–29 |
| Complete workflow and documentation | Diagram drafted; add ACS matching, connect scripts, and document dependencies. | Dec. 3 |
| Complete final report | Summarize findings, methods, and limitations in the README. | Dec. 4–5 |
| Test reproducibility | Run the workflow from a fresh clone and verify the outputs. | Dec. 6 |
| Submit final project | Publish `final-project` and submit the release URL in Canvas. | Dec. 7 |

## Changes to the Project Plan

In response to Milestone 2 feedback. Our TA pointed out that the real risk in our Gaps section is how integration choices affect the validity of our answers. Based on that we plan to make the following changes. We plan to record every integration choice and its rationale. For example, documenting which 311 request types are kept, how missing locations are handled, and how to deal with rows with unclear data/errors. We also will use rates, not raw counts in order to evenly weigh busier areas with those that are slower.

During data profiling, we removed the congestion dataset. Its records cover stretches of street between a start street and an end street, so they do not match well to community areas, and congestion is only estimated from CTA bus data on major streets. Because of this, we took congestion out of our research question. Our new question is: Across Chicago's community areas from 2019 to 2023, how are speeding violations and resident reported road infrastructure problems associated with how often traffic crashes happen and how severe they are, and which areas should the city prioritize for traffic safety funding based on these factors? We still use three linked event datasets (crashes, speed camera violations, and 311 road requests), so the project still meets the three dataset requirement. As mentioned above, we will use rates (per 10,000 residents) instead of raw counts so larger community areas do not look worse just because more people live there. To do this, we'll use an additional census dataset to match areas with population estimates.  We updated ProjectPlan.md to reflect these changes.

## Challenges and How We Are Addressing Them

Challenge: Missing or (0,0) coordinates  
Resolution: Check whether the excluded records cluster in certain areas or times

**Population matching.** Before calculating rates, we will document which ACS estimates we use, how they map to community areas, and which years they represent. We will flag areas without a reliable match rather than report unsupported rates. Rates per 10,000 residents adjust for resident population, not traffic volume. Crash severity will be reported separately; if we use the share of crashes involving injury, we will document how records with unknown injury status are handled.

**Camera coverage and merge validation.** Recorded violations reflect where cameras operate, not all speeding. We will distinguish confirmed zero violations from missing observations or unknown coverage. We will also verify that the merged table has no more than one row per community area and month, count unmatched keys by source, and reconcile event totals before and after the join.

## Individual Contribution Summary: Sophia Kostov

For Milestone 3, I contributed to pre-integration quality assessment and data cleaning. Specifically, I wrote the reports for both and contributed to the specific artifacts for both and addressed any challenges that came up within both of those tasks.

## Individual Contribution Summary: Ariston Liu

For Milestone 3, I updated the project's direction after we decided to remove the congestion dataset. I revised the research question and updated ProjectPlan.md to match our current datasets. I also chose to measure crashes, speed camera violations, and 311 road requests per 10,000 residents to follow our TA's feedback about using rates, and I added the ACS population dataset to make that possible.

## Individual Contribution Summary: Anvith Mulpuri

For Milestone 3, I created the initial status report and committed the [workflow document and diagram](docs/workflow.md). I documented the planned stages from data retrieval through merge validation and updated the timeline to show which tasks are complete and which depend on cleaning and integration. My next steps are to document ACS population matching in the workflow and connect the stage scripts once they are runnable.

## Individual Contribution Summary: Brady Johnson

For Milestone 3, I extracted the datasets from the Chicago datasets website. I then added them into the data folder so Sophia could start cleaning them. Before she cleaned them, I created a data profile so she know how to start cleaning. I mapped out what was good in each data set and how the common link was formatted in each data set. More specifically, I did the data acquisition and the data profiling.
