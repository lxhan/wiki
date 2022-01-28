## Register service as a scalable target
```sh
aws application-autoscaling register-scalable-target --cli-input-json file://aws/autoscale/dev/scalable-target.json
```

## Assign policies for memory and CPU
> After executing command save PolicyARN from output for setting up alarms later

- Memory scale out
```sh
aws application-autoscaling put-scaling-policy --cli-input-json file://aws/autoscale/dev/memory/scale-out.json
```

- Memory scale down
```sh
aws application-autoscaling put-scaling-policy --cli-input-json file://aws/autoscale/dev/memory/scale-down.json
```

- CPU scale out
```sh
aws application-autoscaling put-scaling-policy --cli-input-json file://aws/autoscale/dev/cpu/scale-out.json
```

- CPU scale down
```sh
aws application-autoscaling put-scaling-policy --cli-input-json file://aws/autoscale/dev/cpu/scale-down.json
```

## Register alarms on CloudWatch

- Memory scale out
```sh
aws cloudwatch put-metric-alarm --cli-input-json file://aws/autoscale/dev/memory/alarm-scale-out.json
```

- Memory scale down
```sh
aws cloudwatch put-metric-alarm --cli-input-json file://aws/autoscale/dev/memory/alarm-scale-down.json
```

- CPU scale out
```sh
aws cloudwatch put-metric-alarm --cli-input-json file://aws/autoscale/dev/cpu/alarm-scale-out.json
```

- CPU scale down
```sh
aws cloudwatch put-metric-alarm --cli-input-json file://aws/autoscale/dev/cpu/alarm-scale-down.json
```
