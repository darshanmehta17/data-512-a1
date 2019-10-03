# DATA 512 - Assignment 1 - Data Curation

## Goal
The goal of this assignment is to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from January 1, 2008 through August 30, 2019. We combined data about Wikipedia traffic from two different Wikimedia REST API endpoints (Pageviews and Page Counts) into a single dataset, process the data, and then analyzed it by building a simple visualization. The entire work from data curation to processing and analysis is present in this [Jupyter Notebook](/hcds-a1-data-curation.ipynb). The purpose is to demonstrate best practices for open scientific research in designing and implementing one's project, and make the project fully reproducible by others: from data collection to data analysis.

**Note:** Since July 2015, a new page view definition took effect, which identified all crawler traffic. The new API provided means to elimite this segment of views. As much as possible, we're interested in organic (user) traffic, as opposed to traffic by web crawlers or spiders. So, we filter the crawler traffic by passing ```agent=user``` parameter to the new API. There is a brief period in which both the APIs were functional and there is data on the view count from both. This is reflected in the visualization.

## Dataset
The final dataset located in this [csv](/en-wikipedia_traffic_200801-201908.csv) is the result of a merger of the datasets on page view counts obtained from the two APIs. The process of curation and processing is present in this [Jupyter Notebook](/hcds-a1-data-curation.ipynb). The schema and definition of the columns in this dataset is explained in the table below.

| Column | Value | 
| ------ | ------ |
| year | YYYY | 
| month | MM | 
|pagecount_all_views| Number of page views from all clients acquired from the Legacy Pagecounts API |
|pagecount_desktop_views | Number of page views from desktop clients acquired from the Legacy Pagecounts API |
|pagecount_mobile_views	| Number of page page views from mobile clients acquired from the Legacy Pagecounts API |
|pageview_all_views| Number of page views from all clients acquired from the Pageviews API |
|pageview_desktop_views| Number of page views from desktop clients acquired from the Pageviews API |
|pageview_mobile_views| Number of page views from mobile clients acquired from the Pageviews API |

The raw datasets sources from the APIs are available as ```json``` files with the naming convention ```apiname_accesstype_firstmonth-lastmonth.json```.

## Results
The plot of page views counted over time in the curated dataset is depicted below. More details on the plot can be found in the ```Data Analysis``` section [here](/hcds-a1-data-curation.ipynb#Data-Analysis).

![Page Views on English Wikipedia (x 1,000,000)](/en-wikipedia_traffic_200801-201908.png)

## API Documentation
In order to measure Wikipedia traffic from 2008-2019, we collect data from two different API endpoints, the Legacy Pagecounts API and the Pageviews API.

- The Legacy Pagecounts API ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts)) provides access to desktop and mobile traffic data from December 2007 through July 2016.
- The Pageviews API ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews)) provides access to desktop, mobile web, and mobile app traffic data from July 2015 through last month.

## License of Source Data
The terms of use of the Wikimedia Foundation REST API can be found [here](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions).

## Requirements
- python v3.7+
- pandas v0.23.4+
- matplotlib v2.2.3+
