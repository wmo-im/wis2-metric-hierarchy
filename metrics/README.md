# WIS2 metric hierarchy

## Structure

The structure of the metric hierarchy follows the same logic as the WIS2 topic hierarchy in that it defines the root of a tree for all Global Services and other services and data that are to be monitored, whereas the subtrees can be defined by the service in question.

The primary topic levels are described in the following table. The individual levels are separated by [`_`].

| **Level** | **Name** | **Notes** |
| --- | --- | --- |
| **1** | organization | The root of the monitoring metrics is set fixed to [`wmo`] |
| **2** | program | The second level of the hierarchy names the wmo program for which the metrics apply. WIS 2 related metrics are set to [`wis2`] |
| **3** | programm-service | Name of the service / data feed (for example gb) |

## Labels

All metrics should at least contain the labels [`centre_id`] which indicates whose status this metric refers to, and [`report_by`] the name of the centre reporting this metric.

**Example** wmo\_wis2\_gc\_downloaded\_total\{centre\_id=\"de-dwd-global-cache\",report\_by=\"de-dwd-global-cache\"}

The further required labels are part of the metric definition.

## List of wis2 services
| **Name** | **Description** | **File** |
| --- | --- | --- |
|gb|Metrics related to the Global Brokers|gb.csv
|gc|Metrics related to the Global Cache|gc.csv
|gdc|Metrics related to the Global Discovery Catalogue|gdc.csv
|gm|Metrics related to the Global Monitoring|gm.csv
|sgc|Metrics on the Performance of Global Caches from Sensor Centres|sgc.csv
|sgb|Metrics on the Performance of Global Brokers from Sensor Centres|sgb.csv
|sgdc|Metrics on the Performance of Global Discovery Catalogues from Sensor Centres|sgdc.csv
|sobs|Metrics on the Availability of Observations from Sensor Centres|sobs.csv
