# test-SysOps
Repo with the candidate test



# Questions:

## App Server

**Why do you think different cache times for the nginx cache and for the browser were defined?**

There are different levels of cache. Browser cache helps improve performance by letting browser to cache elements
that not change frequently. For example a company logo's image.
Server or proxy cache are a way to cache elements and respond with the same results to every query and user.

But I do not know why anyone would want to define different cache times.



## Auto-scaling
**Which code have you added to the user-data on launching the instance?**

```
#!/bin/bash

apt-get update -qq
cd /opt
mkdir test
cd test
git clone https://bitbucket.org/Marfeel/appserverpythontestapp.git .
chown -R www-data:www-data /opt/test/
systemctl restart python-app.service
systemctl restart nginx
```



