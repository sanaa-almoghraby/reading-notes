# Amplify and Kinesis
### ANALYTICS

The Analytics category enables you to collect analytics data for your App. The Analytics category comes with built-in support for Amazon Pinpoint and Amazon Kinesis (Kinesis support is currently only available in the Amplify JavaScript library).

### Record event
The Amplify analytics plugin also makes it easy to record custom events within the app. The plugin handles retry logic in the event the device loses network connectivity and automatically batches requests to reduce network bandwidth.

* Flush events
Events have default configuration to flush out to the network every 30 seconds.

### Automatically track sessions
The Amplify analytics plugin records when an application opens and closes. This session information can be viewed either from your local computer's terminal or the AWS Console for Pinpoint.

[MORE SOURCE](https://docs.amplify.aws/lib/analytics/getting-started/q/platform/android/#view-analytics-console)