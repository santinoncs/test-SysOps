**Which is the AMI id of your instance?**

```
ami-f27f2d8b
```


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
