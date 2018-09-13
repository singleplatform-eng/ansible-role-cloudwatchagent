[![Build Status](https://travis-ci.org/singleplatform-eng/ansible-role-cloudwatchagent.svg?branch=master)](https://travis-ci.org/singleplatform-eng/ansible-role-cloudwatchagent)

ansible-role-cloudwatchagent

=========

Ansible role for installing and configuring the CloudWatch CloudWatch Agent
https://galaxy.ansible.com/singleplatform-eng/cloudwatchagent/

Role Variables
--------------
Metrics to be collected, and the params of metrics collection (including collection interval) can be configured in the variable cwa_metrics. The template will convert the yaml into nice_json to create the amazon-cloudwatch-agent.json configuration file.

    Example:


    cwa_metrics:
      agent:
         metrics_collection_interval: 60
         logfile: "/opt/aws/amazon-clouwatch-agent.log"
      metrics:
        metrics_collected:
          disk:
            resources:
              - "/"
              - "/tmp"
            measurement:
             - "used_percent"
             append_dimensions:
                InstanceId: "{{ ansible_ec2_instance_id }}"

Currently this role only supports metrics collection, in future it will also support logs collection as well.

Example Playbook
----------------
    - hosts: all
      become: yes
      roles:
          - ansible-role-cloudwatchagent

Author Information
------------------
[SinglePlatform Engineering](http://engineering.singleplatform.com/)

