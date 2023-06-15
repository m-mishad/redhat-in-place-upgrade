# Red Hat Enterprise Linux 8 Upgrading from RHEL 7.9 to RHEL 8.6 in AWS EC2 instances that are using RHUI.


## Step 1: Planning stage:

##### 1.1 Supported path: 

![](media/Supported-upgrade-path.png)

For more information about supported path: (https://access.redhat.com/articles/4263361)

##### 1.2 Make sure the latest version of RHEL 7 is installed. 
##### 1.3 Make sure valid Redhat subscription is attched. 
##### 1.4 Application compatibility with new OS.
##### 1.5 Analysis of report generated by leapp utility and fixing the issues reported.

## Step 2: Preparing the system for upgrade:


```
cat /etc/redhat-release
uname -a
cat /proc/cpuinfo
getenforce
yum versionlock list
yum versionlock clear
lsblk
df -hT
cat /proc/mounts
cat /etc/fstab
ip a

```



```systemctl --type=service --state=running```

```yum repolist```

```yum list installed```


```yum-config-manager --enable rhui-client-config-server-7```

```yum-config-manager --enable rhel-7-server-rhui-extras-rpms```

```yum -y install rh-amazon-rhui-client leapp-rhui-aws```


```yum update```

```reboot```

```yum install leapp-upgrade```


```wget https://access.redhat.com/articles/3664871```

```tar -xzf leapp-data-22.tar.gz -C /etc/leapp/files && rm leapp-data-22.tar.gz```


```leapp preupgrade --target 8.6 --no-rhsm```



Ref: 
1. (https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/upgrading_from_rhel_7_to_rhel_8/index)

