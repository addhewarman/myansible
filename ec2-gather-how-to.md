1. Login to your ec2 instance, create your playbook
<code>
#mkdir provisioning
#vim provisioning/ec2-gather.yml
- name: Initialize EC2 Instance For '{{ name_web_host }}'
  hosts: localhost
  connection: local
  gather_facts: True
  tasks:
      - name: Get instance ec2 facts
        action: ec2_facts
        register: ec2_facts
      - debug: var=ec2_facts
</code>

2. Let's put your ec2.py in same directory also ec2.private-ip.ini
<code>
#cp ec2.py ec2.private-ip.ini ~/provisioning/
</code>

3. Let's test add some information for it
<code>
#export ANSIBLE_HOST_KEY_CHECKING=False
#export EC2_INI_PATH=./ec2.private-ip.ini
#export AWS_ACCESS_KEY={your aws access key}
#export AWS_SECRET_KEY={your aws secret key}</code>

#~/provisioning/ec2.py --refresh-cache

#ansible-playbook -i local, provisioning/ec2-gather.yml --extra-vars="aws_access_key=$AWS_ACCESS_KEY aws_secret_key=$AWS_SECRET_KEY" -vvvv

<code>your output will be something like this</code>
