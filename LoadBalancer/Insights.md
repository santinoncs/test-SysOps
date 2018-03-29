Steps:



All the responses come from 1 server, the haproxy has this configuration

```
balance uri whole
```

Testing..

```
ST-A138-36LFVH8:MarFeel santiago.nunezcacho$ curl http://34.242.222.27/cgi-bin/test.cgi   
<b>Appserver 2</b>
2018-03-29 16:16:51.092497
2018-03-29 16:16:53.094638
ST-A138-36LFVH8:MarFeel santiago.nunezcacho$ curl http://34.242.222.27/cgi-bin/test.cgi 
<b>Appserver 2</b>
2018-03-29 16:16:51.092497
2018-03-29 16:16:53.094638
ST-A138-36LFVH8:MarFeel santiago.nunezcacho$ 
```

Because the http connection to the nginxs is now comming from a haproxy, we can remove the public IPs or
allow the connections to the http only from the private haproxy IP.
