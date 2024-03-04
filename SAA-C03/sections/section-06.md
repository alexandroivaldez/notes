# EC2 (SAA Level)

Section 6: EC2 - Solutions Architect Associate Level

## Private VS Public VS Elastic IP

Networking has two sorts of IPs:

- IPv4: 1.160.10.240
- IPv6: 1900:4545:3:200:f8ff:fe21:67cf

AWS has support for IPv4 and IPv6.

### Private vs Public IP

- Public IP:
  - The machine can be identified on the internet (www).
  - Unique across the entire web.
  - Can be geo-located easily

- Private IP:
  - Private IP means the machine can only be identified on a private network only.
  - The IP must be unique across the private network.
  - Two different private networks (two companies) can have the same IPs.
  - Machines connect to the internet using a NAT internet gateway.
  - Only a specified range of IPs can be used as private IPs.

### Elastic IP

When you stop and start an EC2 instance, it can change its public IP. So, if you need a fixed public IP for your instance, you need an Elastic IP.

- An elastic IP is a public IPv4 IP that you own or "rent" as long as you don't delete your EC2 instance.
  - You can attach it to one instance at a time. This also allows you to "mask" failures of an instance or software by quickly moving the IP from one instance to another.

- You can only have 5 elastic IP in your account (but you can ask AWS to increase it).

- Overall, try avoiding Elastic IP; poor architectural decision.

## EC2 Placement Groups

## Elastic Network Interfaces (ENI)

