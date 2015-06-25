Kibana AWS AMI with Packer
=============

Install [Packer](https://www.packer.io/) and add it to your PATH.

Create your kibana AMI in AWS, using your access and secret keys.

This also installs [Consul](https://www.consul.io/). This will need to be configured separately as it would be a good
idea to join an existing consul cluster.

```
packer build \
  -var 'aws_access_key=your_key' \
  -var 'aws_secret_key=your_secret' \
  -var 'aws_vpc_id=your_vpc_id' \
  -var 'aws_subnet_id=your_subnet_id' \
  kibana.json
```

Or

```
packer build -var-file='packer_vars.json' kibana.json
```

Extra variables exposed:

* aws_region (defaults to `ap-southeast-2`)
* aws_instance_type (defaults to `t2.small`)
* ami_name_prefix (defaults to `kibana`)
* elastic_version (defaults to `1.4.2`)
* consul_version (defaults to `0.5.0`)

###Troubleshooting

* Make sure you have set the AWS region and the correct source AMI (Ubuntu 14.x recommended) for that region
