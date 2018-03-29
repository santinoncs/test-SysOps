Steps:

1. Install haproxy and awscli
2. Configure the aws cli access and secret key.


If we need to configure the access/secret key in a deploy automation or anything programmatic, we can deploy the 
~/.aws/credentials and ~/.aws/config file.


2. Script to autoscaling
4. Set the script in the crontab.

5. TEST

All the responses come from 1 server, the haproxy has this configuration

```
balance uri whole
```

Testing..

```
$ curl http://34.242.222.27/cgi-bin/test.cgi   
<b>Appserver 2</b>
2018-03-29 16:16:51.092497
2018-03-29 16:16:53.094638
$ curl http://34.242.222.27/cgi-bin/test.cgi 
<b>Appserver 2</b>
2018-03-29 16:16:51.092497
2018-03-29 16:16:53.094638
ST-A138-36LFVH8:MarFeel santiago.nunezcacho$ 
```

6. Enhance security

Because the http connection to the nginxs is now comming from a haproxy, we can remove the public IPs or
allow the connections to the http only from the private haproxy IP.
