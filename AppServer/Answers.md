Steps:

1. Set the unit systemd python app file and enable it.
2. Install nginx
3. clone the repo from github into /opt/test via https
4. chown the contents with the user www-data used.
5. Add a file called default with the server nginx data.
5. Enable gzip

```
curl -H "Accept-Encoding: gzip"  http://localhost/cgi-bin/test.cgi -Ivvv
```

6. Set the proxy pass in order to proxy all the cgi-bin content via nginx
7. Add the cache for the proxied data to 1m

```
root@ip-172-31-40-120:~# date; curl -X GET http://localhost/cgi-bin/test.cgi
Tue Mar 27 18:33:14 UTC 2018
2018-03-27 18:32:52.867050
2018-03-27 18:32:54.869198
root@ip-172-31-40-120:~# date; curl -X GET http://localhost/cgi-bin/test.cgi
Tue Mar 27 18:33:15 UTC 2018
2018-03-27 18:32:52.867050
2018-03-27 18:32:54.869198
root@ip-172-31-40-120:~# date; curl -X GET http://localhost/cgi-bin/test.cgi
Tue Mar 27 18:33:56 UTC 2018
2018-03-27 18:33:56.140171
2018-03-27 18:33:58.142291
root@ip-172-31-40-120:~# 
```

8. Add the cache-control headers.


