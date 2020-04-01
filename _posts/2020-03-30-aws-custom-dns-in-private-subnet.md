---
layout: post
title: 'Service Discovery of EC2 instances in a private subnet'
description: Use Route53 to assign DNS names to your EC2 instances

---

When you boot up your ec2 instances, you get random domain names like `ip-10-0-1-131.eu-west-1.compute.internal`.

You would get a new domain name each time you rebuild your infrastructure. Beyond more sophisticated techologies like Service discovery and serverless frameworks, there is a low tech approach to making your ec2 instances discoverable.

The snippets below use Terraform to demonstrate this.

## Background

When migrating legacy applications to AWS, you are often required to jump through some hoops to get it into production. We were tasked with moving a legacy 3 tier Java application from an on-site hosting provider to AWS.

This migration would consist of multiple steps which would finally lead to the new AWS version processing live traffic. We would aim to recreate the current (bad) infrastructure in AWS and go live with it to minimise risky changes. We would then incrementally change and improve this architecture. The end goal being to run the applications in AWS Fargate and swap out the old IBM / Fujitsu dependencies (such as queueing and databases) for more modern alternatives.

These applications had to be in a private subnet as they weren't allowed to communicate over the public internet. Our solution was to register an instance with Route53 as soon as it's created. We grab output of the instance, specifically the private IP address (like `10.0.1.1`), and use this to create the record in Route53 with a private hosted zone.

## Terraform

If an instance was to be recreated, it would force the Route53 A record to be updated.

```terraform
resource "aws_instance" "foo" {
  ami                    = ...
  instance_type          = "t2.small"
  subnet_id              = var.subnet_id
}

resource "aws_route53_record" "foo_a_record" {
  zone_id = aws_route53_zone.private.zone_id
  name    = "foo.bar.org"
  type    = "A"
  ttl     = "300"
  records = aws_instance.foo.private_ip
}
```

After applying this, from within your private subnet, you will be able to access your aws instance on `foo.bar.org`.

Feel free to hit me up on [twitter](https://twitter.com/emileswarts) with questions!
