#Architecture overview 
this architecture is based on production level highly scalable, and avialable architecture ensuring high security and perventing threats and attacks


##steps creation of this architecture

1)created a costume vpc with cidr block 10.0.0.0/24
2)created four subnets inside vpc for high availablity and fault tolerance
on different AZs 
3)two public subnet and two private subnet
4)create IG(internet gateway) and attached it to vpc for the communication of the resources are inside the vpc to internet
5)created two route table, one public and other private and attached them to public and private subnets respectively 
6)set routs in both the route table
7)created ALB in public subnet 
8)creatd ASG in private subnet and attached to target group 
9)created NAT gateway in public subnet to provide internet access to the private instances launched by ASG
10) created a s3 bucket and uploaded file(html,css,js) and sync these file to the default folder of web server used in templet
11)i used cloudfront for fast delivery of response of the request


###workflow of user`s request 
1)request first comes to cloudfront and cludfront checks it if it cached response then deliver it faster
2)request goes to load balancer from cloudfront and then target group 
3)where the health of registered instances are checked if they are healthy then request is sent to the other wise it sends the massage to auto scaling group and it terminates those instances and creates new one 
4)then it reaches to instances then running webserves inside the instances servers the request to the user
