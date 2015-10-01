#How to manually insert metrics data to Grafana

- Add graphite as data source

In dashboard go to data sources and click add new. Enter this information:
```
Name: graphite-source  
Type: Graphite  
Url: http://localhost:8000  
Access: proxy  
```

- Run a bunch of these with different values each time to send metrics to carbon
```
echo "carbon.agents.graphite-test.metricsReceived 28198 `date +%s`" | nc localhost 2003
echo "carbon.agents.graphite-test.creates 8 `date +%s`" | nc localhost 2003
```

- Create new dashboard

   From Home click button "+ New"  
   Add panel > Graph  
   Click panel title bar > Edit  
   In metric tab change data source from grafana to graphite-source  
   Select the following metric: carbon.agents.graphite-test.metricsReceived  
   You can add another row for the other metric: carbon.agents.graphite-test.creates  
   Click back to dashboard  
