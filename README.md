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
As variavéis abaixo são listadas como padrão. (Veja defaults/main.yml)


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

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a
website (HTML is not allowed).
