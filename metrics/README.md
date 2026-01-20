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

All metrics should at least contain the following labels:
- [`centre_id`] which indicates whose status this metric refers to.
  - For Global Brokers: use the `centre-id` of the WIS2 component where the WIS2 Notification Message originated.
  - For Global Caches: use the `centre-id` of the WIS2 component from where a resource is downloaded and cached, e.g., the origin WIS2 Node (parsed from the 4th field of the WIS2 Topic) or a Global Cache (parsed from the `properties.global-cache` object in the WIS2 Notification Message).
  - For Global Discovery Catalogues: use the `centre-id` of the WIS2 Node where the discovery metadata record originated.
  - For Global Monitors: use the `centre-id` of the WIS2 component that is publishing the metrics being downloaded.
- [`report_by`] the `centre-id` of the WIS2 component reporting this metric.

The `centre-id` for each WIS2 component (WIS2 Node, Global Service, Sensor Centre, etc.) is listed in the [WMO Codes Registry](http://codes.wmo.int/wis/topic-hierarchy/centre-id).

**Example**: `wmo\_wis2\_gc\_downloaded\_total\{centre\_id=\"ca-eccc-msc\",report\_by=\"de-dwd-global-cache\"}` provides a count of the total number of data items that the German Global Cache (`de-dwd-global-cache`) has downloaded from the Meteorological Service of Canada WIS2 Node (`ca-eccc-msc`). 

The further required labels are part of the metric definition.

## List of wis2 services
| **Name** | **Description** | **File** |
| --- | --- | --- |
|gb|Metrics related to the Global Brokers|gb.csv
|gc|Metrics related to the Global Cache|gc.csv
|gdc|Metrics related to the Global Discovery Catalogue|gdc.csv
|gm|Metrics related to the Global Monitoring|gm.csv
|gw|Metrics related to the GTS-to-WIS2 Gateway|gw.csv
|wg|Metrics related to the WIS2-to-GTS Gateway|wg.csv
|sgc|Metrics on the Performance of Global Caches from Sensor Centres|sgc.csv
|sgb|Metrics on the Performance of Global Brokers from Sensor Centres|sgb.csv
|sgdc|Metrics on the Performance of Global Discovery Catalogues from Sensor Centres|sgdc.csv
|sgts|Metrics on the Publication of GTS Data in WIS2 from Sensor Centres|sgts.csv
|sobs|Metrics on the Availability of Observations from Sensor Centres|sobs.csv
