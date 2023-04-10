**To enable logging in your helm**


1. Copy the fluentd folder into your helm directory

2. Copy the Geneva folder into your helm\templates directory

3. Copy the contents of samplevalues.yaml into your helm\values.yaml file.

P.S.
You cannot add this chart as subchart of your helm chart because,
Values.Azure.Extension.Name is set by extension manager at parent chart level, not at global level.

If extension manager would be setting azure values at global level for e.g. by --set Values.global.Azure.Extension.Name="myspringbootclusterextension"
then it would be possible to add this helm as dependency chart because then subcharts can refer this value by Values.global.Azure.Extension.Name.

**In your go pod**
- You can refer following go module which will help you to log diagnostic, metric, telemetry and error event, which are compaitable to fluentd config provided in this repo.
https://github.com/Azure/azure-migrate-discovery-extension-events
-
In your main.go, set zapr logger
````
	ctrl.SetLogger(getLogger())
````
  
````
// GetLogger return a DelegatingLogger.
func getLogger() logr.Logger {
	encConfig := zapcore.EncoderConfig{
		MessageKey:     "Message",
		LevelKey:       "LogLevel",
		TimeKey:        "Timestamp",
		NameKey:        "Name",
		CallerKey:      "Caller",
		StacktraceKey:  "Stacktrace",
		LineEnding:     "\n",
		EncodeLevel:    zapcore.CapitalLevelEncoder,
		EncodeCaller:   zapcore.FullCallerEncoder,
		EncodeDuration: zapcore.SecondsDurationEncoder,
		EncodeTime:     zapcore.ISO8601TimeEncoder,
	}
	return zap.New(zap.UseDevMode(false), zap.Encoder(zapcore.NewJSONEncoder(encConfig)))
}

````

- You are free to use your own way of logging the events.
- Just make sure the routing in fluentd config is in sync with what you are implementing. 

**For understanding fluentdconfig.**

1. Follow FluentdReadMe.md

**For understanding whether amacoreagent container is getting accessing token to be presented to GCS service.**

1. Follow TestReadMe.md

**For full architecture overview**

1. https://microsoftapc-my.sharepoint.com/:w:/g/personal/rahasija_microsoft_com/EYvrGyrBTX9MndkGB2GuXj0BJvM45wzaTBEAySah86N2PQ?e=PO9KXR
