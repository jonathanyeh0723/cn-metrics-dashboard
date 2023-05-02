# cn-metrics-dashboard
Using Prometheus, Jaeger, and Grafana to monitor, trace and visualize the application that is deployed on a Kubernetes cluster.

## Verify the monitoring installation

run kubectl command to show the running pods and services for all components. 
```
$ kubectl get all -n monitoring
```

## Setup the Jaeger and Prometheus source

Expose Grafana to the internet and then setup Prometheus as a data source.
```
$ kubectl port-forward -n monitoring prometheus-grafana-6c6f7bfc99-w2r7w --address 0.0.0.0 3000
```

## Create a Basic Dashboard

Create a dashboard in Grafana that shows Prometheus as a source.
```
$ kubectl port-forward svc/frontend-service 8080:8080
```

See attached.

## Creating SLI metrics.

It is important to know why we want to measure certain metrics for our customer. Describe in detail 5 metrics to measure these SLIs.

SLIs, or Service Level Indicators, are metrics that are used to measure the performance of a service. In the context of an SLO for monthly uptime and request response time, SLIs would be the specific metrics that are used to measure these two aspects of service performance.

For example, an SLI for monthly uptime could be the percentage of time that the service is available in a given month. This could be measured by monitoring the service and recording the amount of time that it is up and running versus the amount of time that it is down or unavailable.

Similarly, an SLI for request response time could be the average amount of time it takes for the service to respond to a request. This could be measured by monitoring the service and recording the amount of time it takes to respond to each request, then calculating the average response time.

By tracking these SLIs, you can get a better understanding of how well your service is performing in terms of uptime and response time, and use this information to set SLOs, or Service Level Objectives, for these metrics. SLOs are specific targets that you set for your SLIs, and they help you ensure that your service is meeting the performance standards that you need to meet your business goals.

For example, you might set an SLO for monthly uptime of 99.9%, which means that you want your service to be available for at least 99.9% of the time in a given month. You might also set an SLO for request response time of 200 milliseconds, which means that you want your service to respond to requests in no more than 200 milliseconds on average.

## Creating SLI metrics.

1. Latency: This metric measures the time it takes for a request to be processed and a response to be returned. It is a critical metric for applications that require fast response times, such as real-time data processing or online gaming.

2. Error rate: This metric measures the percentage of requests that result in errors. It is important to track this metric to ensure that errors are caught and addressed before they impact users.

3. Throughput: This metric measures the number of requests that can be processed by the application in a given time period. It is important to track this metric to ensure that the application can handle the expected load.

4.  Availability: This metric measures the percentage of time that the application is available and functioning properly. It is important to track this metric to ensure that the application is meeting its uptime requirements.

5. Resource utilization: This metric measures the amount of resources, such as CPU, memory, and disk space, that the application is using. It is important to track this metric to ensure that the application is not overloading the system and causing performance issues.

