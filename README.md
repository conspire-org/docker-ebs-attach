docker-ebs-attach
==============

Docker container that attaches an EBS volume to the local ec2 instance.

Usage: 

```
docker run -it --rm leg100/ebs-attach \
--volumeid vol-123123 \
--device /dev/xvdf \
--region eu-west-1
```

Note: it relies on the ec2 instance possessing an IAM profile with the following privileges:

 - ec2:AttachVolume
 - ec2:DetachVolume

Provision your EC2 instances with the IAM role "ebs-association".  EBS volumes must also be formatted before they can be used.

1. Provision EBS volume in the correct region.
2. Attach to any host (ops or target are fine).
3. Format with `sudo mkfs -t ext4 device_name` where device name is the device you attached this EBS volume to (e.g., /dev/xvdc).

(Adapted from http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-using-volumes.html)
