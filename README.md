# test-SysOps
Repo with the candidate test



# Questions:

## App Server

**Why do you think different cache times for the nginx cache and for the browser were defined?**



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



