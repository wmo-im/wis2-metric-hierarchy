# WIS2 metric hierarchy

## Overview

The WIS2 metric hierarchy provides a central classification and categorization scheme used by WIS2 Global Services to publish their monitoring metrics in the OpenMetrics format.

## Global Monitoring

The WIS2 Global Monitoring fetches metrics from all WIS2 Global Services. In order to maintain a common naming scheme this project documents the relevant metrics.

## Structure

The structure of the metric hierarchy follows the same logic as the WIS2 topic hierarchy in that it defines the root of a tree for all Global Services and other services and data that are to be monitored, whereas the subtrees can be defined by the service in question.

The primary topic levels are described in the following table. The individual levels are separated by [`_`].

| **Level** | **Name** | **Notes** |
| --- | --- | --- |
| **1** | organization | The root of the monitoring metrics is set fixed to [`wmo`] |
| **2** | program | The second level of the hierarchy names the wmo program for which the metrics apply. WIS 2 related metrics are set to [`wis2`] |
| **3** | service | Name of the service / data feed |

## Labels

All metrics should at least contain the label [`center`] which indicates whose status this metric refers to. 

**Example** wmo\_wis2\_gc\_messagesreceived\{center=deu\}

The labels are defined in the corresponding subdirectory of the metric names
