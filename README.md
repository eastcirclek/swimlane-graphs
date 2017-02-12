# swimlane-graphs

The purpose of HiveSummary, PrestoSummary, and SparkSummary is to draw
swimlane graphs which share the same x axis with ganglia graphs.
Please take a look at the screenshot images: hive-summary.png and spark-summary.png.

Requirement of each file is as follows:
- Ganglia and Ganglia Web Frontend are required for all *summary.html
- Hive requires to save job history in Application Timeline Service (ATS)
- Spark requires to save job history in Spark HistoryServer
- Presto requires nothing (the script directly connects to a coordinator)

Note that *summary.html reads from Ganglia the following metrics:
- cpu_report (default)
- network_stack_report (custom)
- disk_throu_report (custom)

To extract network and disk throughput graphs,
copy the following to files to /usr/share/ganglia-webfrontend/graph.d/:
- network_stack_report.json
- disk_through_report.json

You must modify disk_through_report.json to specify your disk devices.
You'd visit the following link to see how to monitor disk throughput in Ganglia:
http://eastcirclek.blogspot.kr/2015/10/monitoring-disk-throughput-using-ganglia.html
