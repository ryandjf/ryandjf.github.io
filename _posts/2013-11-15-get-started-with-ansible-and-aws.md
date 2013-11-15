---
layout: post
title: 'Get started with Ansible and AWS'
tags: 
- Ansible
- AWS
- DevOps
---
Ansible is another simple way to automate applicaiton and configuration deployment. It is similar to Chef except that Chef is using cookbook, recipe (food) as metaphor and Ansible is using playbook, play (music) instead. Both Ansible and Chef have good integration with AWS.

One powerful feature of Ansible is that it doesn't rely on deploying client to your systems to manage them(Chef will deploy chef client to systems). Ansible will just manage your systems listed in Ansible's inventory file. One example inventory file looks like this:

<pre>
[webservers]
foo.example.com
[dbservers]
bar.example.com
</pre>

But if you are working with AWS, your systems will come and go quickly. Maintaining an inventory file might not be the best approach. Ansible provides AWS EC2 External Inventory Script to manage this kind of dynamic inventory.

Let's try to connect our AWS instances with Ansible. You can check the [official document](http://www.ansibleworks.com/docs/guide_aws.html) for boto installation and configuration. Here are simple steps you can follow:
1. Install Ansible
2. Install Boto
3. Set env variable AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY to your AWS credential
4. Launch an EC2 instance in any region (e.g. us-east-1a) with security group (e.g. sg-123456) and key pair (e.g. mykeypair)
5. Make sure inbound rule for SSH is applied for your security group
6. Save your key pair pem file to a secure location (e.g. ~/.ssh/mykeypair.pem)
7. Make sure you have AWS EC2 External Inventory Script(ec2.py) available. Check [document](http://www.ansibleworks.com/docs/intro_dynamic_inventory.html#example-aws-ec2-external-inventory-script) for details
8. Run command "ansible -i ec2.py -u ubuntu --private-key=~/.ssh/mykeypair.pem us-east-1a -m ping" to check the connection with your EC2 instance. (Suppose you launched an Ubuntu instance to us-east-1a region, you can replace the argument with your specific case)
9. Here are example output for my instance:
<pre>
ec2-54-235-41-126.compute-1.amazonaws.com | success >> {
    "changed": false,
    "ping": "pong"
} 
</pre>