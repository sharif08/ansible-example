ROLE
=========

This role is used to prepare freeipa server(ldap server)

Role Variables
--------------

*    internal_ldap_server_master01_ip: "{{ hostvars[groups.ldapserver[0]].host_ip }}"
*    internal_ldap_domain: "{{ host_domain }}"
*    internal_ldap_server_admin_pass: "{{ ldap_server.password }}"
*    inventory_ldap_client_host_ip: "{{ ipa_client_ip }}"
*    internal_ldap_server_docker_name: "{{ hostvars[groups.ldapserver[0]].base.docker.ldap_server.container_name }}"
*    internal_freeipa_client_server: "{{ hostvars[groups.ldapserver[0]].host_fqdn }}"
*    internal_freeipa_client_realm: "{{ host_domain }}"
*    internal_freeipa_client_password: "{{ ldap_server.password }}"
*    internal_freeipa_client_fqdn: "{{ ipa_client_fqdn }}"
*    inventory_hostname_short: '{{ inventory_hostname.split(".")[0] }}'



Dependencies
------------

* role: docker_install

License
-------
BSD


Playbook
--------

- hosts: ldapserver
  remote_user: "{{ admin.user }}"
  gather_facts: no
  become: yes

  roles:
    - freeipa_prepare_client

  vars:
    ipa_client_fqdn:                  #ipa_client_fqdn: vie01-bastion01.r3c.mgms
    ipa_client_ip:                     #ipa_clint_ip: 10.60.10.20


Syntax:
------
* How to run the freeipa Playbook, check the playbook file location first.
  * ansible-playbook playbooks/ldap_server/client_install.yml -i inventory/dc01/hosts -e ipa_client_fqdn=  -e ipa_client_ip= -K --ask-vaul-pass --check

* Check ansible lint for syntax check
  * ansible-lint roles/freeipa_server


