Elasticearch
=========

[![Build Status](https://travis-ci.org/jeduoliveira/ansible-role-elasticsearch.svg?branch=master)](https://travis-ci.org/jeduoliveira/ansible-role-elasticsearch) | [![Ansible Role](https://img.shields.io/ansible/role/11572.svg?maxAge=2592000)](https://galaxy.ansible.com/jeduoliveira/elasticsearch/)

Uma ansible role que instala o [ElasticSearch](https://www.elastic.co/products/elasticsearch) para atender o framework [lumisportal](https://lumisxp.lumis.com.br/doc/lumisportal/11.2.0/pt-BR/lumis.installation_and_configuration.system_requirements.html) no RedHat/CentOS.

Requirements
------------

É necessário JAVA JDK instalado. Veja [jeduoliveira.zulu_openjdk](https://github.com/jeduoliveira/ansible-role-zulu-openjdk) role tem instruções para instalar o Zulu OpenJDK.


Role Variables
--------------
As variáveis abaixo são listadas como padrão. (Veja defaults/main.yml)

    elasticsearch_package_state: present
    elasticsearch_service_state: started
    elasticsearch_service_enabled: true

    elasticsearch_version: 6.2.2

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

    - hosts: all
      gather_facts: True

      roles:    
        - role: ansible-role-elasticsearch
          elasticsearch_version: 6.2.2
          elasticsearch_heap: 2g
          elasticsearch_logger_action_level: error 

License
-------

MIT / BSD

Author Information
------------------

Está role foi criada em 2019 por [Jorge Eduardo](https://www.linkedin.com/in/jorgeeduardo/).