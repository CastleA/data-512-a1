# data-512-a1
Human Centered Design - Assignment 1

# The goal of the project
The goal of this assignment was to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from January 1 2008 through August 30 2021. 

The purpose was to demonstrate best practices for open scientific research in designing and implementing a project such that it is fully reproducible by others: from data collection to data analysis.

# Data source
Wikipedia page traffic was acquired from two different Wikimedia REST API endpoints found at the [Wikimedia Foundation REST API](https://wikimedia.org/api/rest_v1/#/):
- Legacy Pagecounts, [documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts)
- Pageviews, [documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews)


Content accessed via this API is licensed under the [CC-BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) and [GFDL](https://www.gnu.org/licenses/fdl-1.3.html) licenses. Additionally, take notice of the Wikimedia Foundation REST API [Terms of Use](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions).

# Processed data
The final data file, en-wikipedia_traffic_200712-202108.csv, is both available in the repo and fully reproducible via the included Jupyter Notebook, hcds-a1-data-curation.ipynb. To run the notebook you will need a computer with python, jupyter notebook, and pandas installed. 

## Data contains
The csv, en-wikipedia_traffic_200712-202108.csv, contains 8 columns. The first two associated with the year and month the views occurred in:
- year, in the format YYYY
- month, in the format MM

The columns beginning with prefix 'pagecount' are associated with queries to the Legacy Pagecounts endpoint:
- pagecount_all_views, integer count
- pagecount_desktop_views, integer count
- pagecount_mobile_views, integer count

The columns beginning with prefix 'pageviews' are associated with queries to the Pageviews endpoint:
- pageview_all_views, integer count
- pageview_desktop_views, integer count
- pageview_mobile_views, integer count

For both endpoints 'all_views' corresponds to the sum of desktop and mobile views, as reported by that particular endpoint.

## Data quirks
The availability of data across time from each endpoint and of each types varies. For example, mobile views become available from the Legacy Pagecounts endpoint well after desktop views. Additionally, views from the two endpoints overlap for a period. Refer to the csv file to see exactly how the data availability varies.

Views from the Pageviews endpoint differs as well in that it enables the query to be limited to access identified as being by users and excluding accesses by automated means. The Legacy Pagecounts endpoint does not offer this distinction and, in that way, is not directly comparable to the data from Pageviews.
