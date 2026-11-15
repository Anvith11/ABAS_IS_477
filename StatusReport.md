## Data Profiling
Crashes - Lots of data we can use. Includes speed limits, curve, type of crash. Address is already separated by number, direction, and name, so integration should be easier.
Congestion - Was organized in chunks of streets. It had a start street and an ending street, so it would be hard to integrate. We made the decision to exclude this data set. Also, only gives bus count to help estimate congestion time, we do not have historical Chicago data to help us estimate.
Speed Camera - Has location not separated out, but does include number, direction, and name. Has coordinates and number of violations additionally. This will be a very crucial dataset for us because we will be able to tell which areas are high speed.
311 Service Requests - This dataset was originally 14,000,000 rows. This is because it included all requests from aviation noise complaints to leaf removals, and waste complaints. I filtered it down to only include requests that involved CDOT - Department of Transportation. These requests involve pothole notices, sign repairs, road repair requests, etc. Has street address with number, direction, and name, but it is not separated out.

