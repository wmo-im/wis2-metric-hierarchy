# WIS2 metric hierarchy

## Structure

The structure of the metric hierarchy follows the same logic as the WIS2 topic hierarchy in that it defines the root of a tree for all Global Services and other services and data that are to be monitored, whereas the subtrees can be defined by the service in question.

The primary topic levels are described in the following table. The individual levels are separated by `_`.

| **Level** | **Name** | **Notes** |
| --- | --- | --- |
| **1** | organization | The root of the monitoring metrics is set fixed to `wmo` |
| **2** | program | The second level of the hierarchy names the wmo program for which the metrics apply. WIS2 related metrics are set to `wis2` |
| **3** | programm-service | Name of the service / data feed (e.g. `gb`) |

## Labels

All metrics should at least contain the following labels:
- `centre_id` which indicates whose status this metric refers to
  - For Global Brokers: use the `centre-id` of the WIS2 component where the WIS2 Notification Message originated
  - For Global Caches: use the `centre-id` of the WIS2 component from where a resource is downloaded and cached, e.g., the origin WIS2 Node (parsed from the 4th field of the WIS2 Topic) or a Global Cache (from `properties.global-cache` in the WIS2 Notification Message)
  - For Global Discovery Catalogues: use the `centre-id` of the WIS2 Node where the discovery metadata record originated
  - For Global Monitors: use the `centre-id` of the WIS2 component that is publishing the metrics being downloaded
- `report_by` which indicates the `centre-id` of the WIS2 component reporting this metric

The `centre-id` for each WIS2 component (WIS2 Node, Global Service, Sensor Centre, etc.) is listed in the [WMO Codes Registry](http://codes.wmo.int/wis/topic-hierarchy/centre-id).

**Example**: `wmo_wis2_gc_downloaded_total{centre_id="ca-eccc-msc",report_by="de-dwd-global-cache"}` provides a count of the total number of data items that the Deutscher Wetterdienst (Germany) Global Cache Service (`de-dwd-global-cache`) has downloaded from the Environment and Climate Change Canada, Meteorological Service of Canada WIS2 Node (`ca-eccc-msc`).

The further required labels are part of the metric definition.

## List of WIS2 services

| **Name** | **Description** | **File** |
| --- | --- | --- |
|gb|Metrics related to Global Brokers|[gb.csv](gb.csv)
|gc|Metrics related to Global Cache|[gc.csv](gc.csv)
|gdc|Metrics related to Global Discovery Catalogue|[gdc.csv](gdc.csv)
|gm|Metrics related to Global Monitoring|[gm.csv](gm.csv)
|grep|Metrics related to Global Replay|[grep.csv](grep.csv)
|gw|Metrics related to GTS-to-WIS2 Gateways|[gw.csv](gw.csv)
|wg|Metrics related to WIS2-to-GTS Gateways|[wg.csv](wg.csv)
|scgc|Metrics on the Performance of Global Caches from Sensor Centres|[scgc.csv](scgc.csv)
|scgb|Metrics on the Performance of Global Brokers from Sensor Centres|[scgb.csv](scgb.csv)
|scgdc|Metrics on the Performance of Global Discovery Catalogues from Sensor Centres|[scgdc.csv](scgdc.csv)
|scgrep|Metrics on the Performance of Global Replays from Sensor Centres|[scgrep.csv](scgrep.csv)
|scgts|Metrics on the Publication of GTS Data in WIS2 from Sensor Centres|[scgts.csv](scgts.csv)
|scobs|Metrics on the Availability of Observations from Sensor Centres|[scobs.csv](scobs.csv)
