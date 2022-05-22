For this application I used the `Custom-App` provided by [TrueCharts](https://truecharts.org/manual/Quick-Start%20Guides/01-Adding-TrueCharts/).

- Available under the `stable` train

<br />

## Container 

**Container Repository**
```
bbilly1/tubearchivist
```
**Container Tag**
```
latest
```

![!Container: Tube](ta_container.png)

<br />

## Environment Variables

**Name**
```
ES_URL
```
**Value**
```
http://ta-elastic-custom-app.ix-ta-elastic.svc.cluster.local:9200
```
<br />

**Name**
```
REDIS_HOST
```
**Value**
```
ta-redis-custom-app.ix-ta-redis.svc.cluster.local
```

![!env1: Tube](ta-env1.png)

**Name**
```
TA_USERNAME
```
**Value**
```
USERNAME
```

<br />

**Name**
```
TA_PASSWORD
```
**Value**
```
PASSWORD
```

<br />

**Name**
```
ELASTIC_PASSWORD
```
**Value**
```
verysecret
```

![!env1: Tube](ta-env2.png)

<br />


## Networking

**Target Port**
```
8000
```
**Port**
```
8000
```

![!Networking: Tube](ta-networking.png)

<br />

## Storage

- Used the same dataset we created earlier
- This is where your data, or videos are going to be actually stored
- You could instead use PVC if you would like to, but since my applications are not on the same pool as my storage tank, it would be a bad idea for me personally

Ensure the mountpath is:
```
/youtube
```

TubeArchivist specifically looks to that mount point, its required

![!Storage: Tube](ta-storage_data.png)

<br />

- Used pvc just for the cache, its likely to just be small files the user will never have to interact with anyway

Ensure the mountpath is:
```
/cache
```


![!Storage: Tube](ta-storage_config.png)


<br />

## Security

Running the application without user:group `0` or `root`, resulted in a Django import error.

![!Storage: Tube](ta-security1.png)

![!Storage: Tube](ta-security2.png)

<br />