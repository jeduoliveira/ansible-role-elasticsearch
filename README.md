Elasticearch
=========

[![Build Status](https://travis-ci.org/jeduoliveira/ansible-role-elasticsearch.svg?branch=master)](https://travis-ci.org/jeduoliveira/ansible-role-elasticsearch)


A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should
be mentioned here. For instance, if the role uses the EC2 module, it may be a
good idea to mention in this section that the boto package is required.

Role Variables
--------------
As variáveis abaixo são listadas como padrão. (Veja defaults/main.yml)

    elasticsearch_version: '6.2.2'
    elasticsearch_package_state: present

    elasticsearch_service_state: started
    elasticsearch_service_enabled: true

    elasticsearch_network_host: 0.0.0.0
    elasticsearch_http_port: 9200

    elasticsearch_cluster_name: lumisportal
    elasticsearch_node_name: node-1

    elasticsearch_data: /var/lib/elasticsearch
    elasticsearch_logs: /var/log/elasticsearch

    elasticsearch_heap: 512m

    elasticsearch_logger_action_level: info

As variáveis listadas como vars (veja em vars/main.yml)

    elasticsearch_logger_config:
      - regexp: '^logger.action.level = '
        line: 'logger.action.level = {{ elasticsearch_logger_action_level }}'

    elasticsearch_jvm:
      - regexp: '^-Xms'
        line: -Xms{{ elasticsearch_heap }}
      - regexp: '^-Xmx'
        line: -Xmx{{ elasticsearch_heap }}

Dependencies
------------

    dependencies:
      - jeduoliveira.zulu_openjdk


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: roles/ansible-role-elasticsearch, x: 42 }

License
-------

MIT / BSD

Author Information
------------------

Está role foi criada em 2019 por [Jorge Eduardo](https://www.linkedin.com/in/jorgeeduardo/).