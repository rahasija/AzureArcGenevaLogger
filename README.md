**To enable logging in your helm**


1. Copy the fluentd folder into your helm directory

2. Copy the Geneva folder into your helm\templates directory

3. Copy the contents of samplevalues.yaml into your helm\values.yaml file.

P.S.
You cannot add this chart as subchart of your helm chart because,
Values.Azure.Extension.Name is set by extension manager at parent chart level, not at global level.

If extension manager would be setting azure values at global level for e.g. by --set Values.global.Azure.Extension.Name="myspringbootclusterextension"
then it would be possible to add this helm as dependency chart because then subcharts can refer this value by Values.global.Azure.Extension.Name.




**For understanding fluentdconfig.**

1. Follow FluentdReadMe.md

**For understanding whether amacoreagent container is getting accessing token to be presented to GCS service.**

1. Follow TestReadMe.md

For full architecture overview
https://microsoftapc-my.sharepoint.com/:w:/g/personal/rahasija_microsoft_com/EYvrGyrBTX9MndkGB2GuXj0BJvM45wzaTBEAySah86N2PQ?e=PO9KXR
