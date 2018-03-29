---
layout: post
title:  "Load Balancer and Autoscaling service in AWS Console"
description: "Commands to create a Load Balancer and autoscaling service in AWS Console"
date:   2018-03-30
categories: aws
---

### Create the security group

```sh
$ aws ec2 create-security-group --group-name myELBSG --description "ELB Security Group"
{
    "GroupId": "sg-cbb096b2"
}
```

```
$ aws ec2 authorize-security-group-ingress --group-id sg-cbb096b2 --protocol tcp --port 80 --cidr 0.0.0.0/0
```

### Create Load Balancer

Checking the available subnets we create the load balancer.

```sh
$ aws ec2 describe-subnets
{
    "Subnets": [
        {
            "AvailabilityZone": "us-west-1c",
            "AvailableIpAddressCount": 4091,
            "CidrBlock": "172.31.16.0/20",
            "DefaultForAz": true,
            "MapPublicIpOnLaunch": true,
            "State": "available",
            "SubnetId": "subnet-46eb9621",
            "VpcId": "vpc-e2d77185",
            "AssignIpv6AddressOnCreation": false,
            "Ipv6CidrBlockAssociationSet": []
        },
        {
            "AvailabilityZone": "us-west-1b",
            "AvailableIpAddressCount": 4089,
            "CidrBlock": "172.31.0.0/20",
            "DefaultForAz": true,
            "MapPublicIpOnLaunch": true,
            "State": "available",
            "SubnetId": "subnet-39f37d62",
            "VpcId": "vpc-e2d77185",
            "AssignIpv6AddressOnCreation": false,
            "Ipv6CidrBlockAssociationSet": []
        }
    ]
}

$ aws elb create-load-balancer --load-balancer-name myELB --listeners Protocol=HTTP,LoadBalancerPort=80,InstanceProtocol=HTTP,InstancePort=80 --subnets subnet-46eb9621 subnet-39f37d62
{
    "DNSName": "myELB-843462165.us-west-1.elb.amazonaws.com"
}
```

### Create the Autoscaling

We need to check the available zones

```sh
$ aws autoscaling create-launch-configuration --launch-configuration-name myAutoScalingLaunchConfig --image-id ami-bf5540df --instance-type t2.micro

$ aws ec2 describe-availability-zones
{
    "AvailabilityZones": [
        {
            "State": "available",
            "Messages": [],
            "RegionName": "us-west-1",
            "ZoneName": "us-west-1b"
        },
        {
            "State": "available",
            "Messages": [],
            "RegionName": "us-west-1",
            "ZoneName": "us-west-1c"
        }
    ]
}

$ aws autoscaling create-auto-scaling-group --auto-scaling-group-name myAutoScaling --launch-configuration-name myAutoScalingLaunchConfig --availability-zones "us-west-1b" "us-west-1c" --load-balancer-names myELB --max-size 5 --min-size
2 --desired-capacity 3
```

### See the autoscaling

```sh
$ aws autoscaling describe-auto-scaling-groups
```
