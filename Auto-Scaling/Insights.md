Steps:

1. First create an ami from the instance.  ( Removing the /opt/test first )
2. Launch an instance from this ami and set the user-data necessary to clone the repo
3. Create a security group linked to default VPC that accepts connections on ports 22 and 80

```
appserver
```


4. Create an auto-scaling group with a fixed number of 2 instances with your AppServer AMI 
and the appropriate set up of user-data to clone the repository.



I will create it without a LB. So requests wont be balanced. You should point to the public IP
of each of the servers to get to them.


Autoscaling group : Appserver_ASG
Launch configuration: Appserver_LC

You need to link the Autoscaling group with a launch configuration, that is, a sort of an instance template when you
can set the image , the user-data and the security group..
