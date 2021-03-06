Steps:

1. Set the unit systemd python app file and enable it.
2. Install nginx
3. clone the repo from github into /opt/test via https
4. chown the contents with the user www-data used.
5. Add a file called default with the server nginx data.
6. Set the proxy pass in order to proxy all the cgi-bin content via nginx
7. Enable gzip via 


```gzip_proxied any;```

Testing...

```
curl -H "Accept-Encoding: gzip"  http://localhost/cgi-bin/test.cgi -Ivvv
```

8. Add the cache for the proxied data to 1m

```
root@ip-172-31-34-50:/opt# date; curl -X GET http://localhost/cgi-bin/test.cgi
Thu Mar 29 14:11:15 UTC 2018
2018-03-29 14:11:10.660453
2018-03-29 14:11:12.662600
root@ip-172-31-34-50:/opt# date; curl -X GET http://localhost/cgi-bin/test.cgi
Thu Mar 29 14:11:34 UTC 2018
2018-03-29 14:11:10.660453
2018-03-29 14:11:12.662600
root@ip-172-31-34-50:/opt# date; curl -X GET http://localhost/cgi-bin/test.cgi
Thu Mar 29 14:12:49 UTC 2018
2018-03-29 14:12:49.526692
2018-03-29 14:12:51.528817
root@ip-172-31-34-50:/opt# 
```

9. Add the cache-control headers.

```
root@ip-172-31-34-50:~# curl -X GET http://localhost/index.html -I
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 29 Mar 2018 14:30:10 GMT
Content-Type: text/html
Content-Length: 114
Last-Modified: Thu, 29 Mar 2018 13:27:55 GMT
Connection: keep-alive
Vary: Accept-Encoding
ETag: "5abce9db-72"
Expires: Thu, 29 Mar 2018 15:30:10 GMT
Cache-Control: max-age=3600
Cache-Control: public
Accept-Ranges: bytes

root@ip-172-31-34-50:~# curl -X GET http://localhost/cgi-bin/test.cgi -I
HTTP/1.1 200 Script output follows
Server: nginx
Date: Thu, 29 Mar 2018 14:30:14 GMT
Content-Type: text/html
Transfer-Encoding: chunked
Connection: keep-alive
Vary: Accept-Encoding
Expires: Thu, 29 Mar 2018 14:40:14 GMT
Cache-Control: max-age=600
Cache-Control: public

root@ip-172-31-34-50:~# 
```
