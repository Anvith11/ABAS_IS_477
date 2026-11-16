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


## Updated Timeline

Pre-Integration Quality Assessment: Complete
Data Cleaning: In Progress


## Changes to the Project Plan

In response to Milestone 2 feedback. Our TA pointed out that the real risk in our Gaps section is how integration choices affect the validity of our answers. Based on that we plan to make the following changes. We plan to record every integration choice and its rationale. For example, documenting which 311 request types are kept, how missing locations are handled, and how to deal with rows with unclear data/errors. We also will use rates, not raw counts in order to evenly weigh busier areas with those that are slower. 



## Challenges and How We Are Addressing Them

Challenge: Missing or (0,0) coordinates
Resolution: Check whether the excluded records cluster in certain areas or times


## Individual Contribution Summary: Sophia Kostov

For Milestone 3, I contributed to pre-integration quality assessment and data cleaning. Specifically, I wrote the reports for both and contributed to the specific artifacts for both and addressed any challenges that came up within both of those tasks.

