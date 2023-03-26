For understanding fluentdconfig.
Follow FluentdReadMe.md

For understanding whether amacoreagent container is getting accessing token to be presented to  GCS service.
Follow TestReadMe.md

To use it in your helm
Copy the fluentd folder into your helm directory
Copy the Geneva folder into your helm\templates directory
Copy the contents of samplevalues.yaml into your helm/values.yaml file.

P.S.
You cannot add this chart as subchart of your helm chart because,
 Values.Azure.Extension.Name is set by extension manager at parent chart level, not at global level.

If extension manager would be setting azure values at global level for e.g. by --set Values.global.Azure.Extension.Name="myspringbootclusterextension"
then it would be possible to add this helm as dependency chart because then subcharts can refer this value by Values.global.Azure.Extension.Name.


