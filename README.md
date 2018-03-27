# test-SysOps
Repo with the candidate test



h2. Questions:

h4. App Server

Why do you think different cache times for the nginx cache and for the browser were defined?




h4. Which code have you added to the user-data on launching the instance?

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
