# AWS-Pingdom-Delay-Alerts-StepFunction
A serverless AWS application that integrates site alerts through pingdom with SNS topics in AWS. The idea is to allow a configuration layer for alerting. The application receives Pingdom site alerts via a Lambda which then passes off the payload to the Step Function below. This then handles routing and passes it off to the relevant alerting endpoints and support queues. 

It has the capabiliity to route alerts depending on support level (out-of-hours etc..) and adds a delay step to prevent call-outs on breif outages. 

![Pingdom Alerts StepFunction](https://github.com/Fred-Luckham/AWS-Pingdom-Delay-Alerts-StepFunction/blob/main/stepfunctions_graph.png?raw=true)

This state machine requires the following Lambdas in order to function:

- ![AlertingPingdomInbound](https://github.com/Fred-Luckham/AWS-Pingdom-Delay-Alerts-Inbound)
- ![AlertingPingdomCheckServiceLevel](https://github.com/Fred-Luckham/AWS-Pingdom-Delay-Alerts-CheckServiceLevel)
- ![AlertingPingdomCheckExecutions](https://github.com/Fred-Luckham/AWS-Pingdom-Delay-Alerts-CheckExecutions)
- AlertingPingdomOpsgenie
- AlertingPingdomSNS
