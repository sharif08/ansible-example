Role Name
=========

This role is used to create replica for Freeipa Server.

Requirements
------------

Freeipa Server 

Role Variables
--------------
*    internal_ldap_server_master02_domain: "{{ hostvars[groups.ldapserver[1]].host_domain }}"
*    internal_ldap_server_master02_dns: "{{ hostvars[groups.ldapserver[1]].ldap_server_dns }}"
*    internal_ldap_server_master01_hostname: "{{ hostvars[groups.ldapserver[0]].host_name }}"
*    internal_ldap_server_master01_ip: "{{ hostvars[groups.ldapserver[0]].host_ip }}"
*    internal_ldap_server_master02_ip: "{{ hostvars[groups.ldapserver[1]].host_ip }}"
*    internal_ldap_server_docker_name: "{{ base.docker.ldap_server.container_name }}"
*    internal_ldap_server_docker_image: "{{ base.docker.ldap_server.image }}"
*    internal_ldap_server_docker_tag: "{{ base.docker.ldap_server.tag }}"
*    internal_docker_restart_policy: "{{ base.docker.restart_policy }}"
*    internal_ldap_server_admin_pass: "{{ ldap_server.password }}"
*    internal_host_user: "{{ system.admin_user }}"


Dependencies
------------

The role dependencie are:

* role: docker_install
* role: freeipa_install

Syntax check
------------
* How to run the freeipa Playbook, check the playbook file location first.
  * ansible-playbook playbooks/ldap_server_replica/ldap_master_replica.yml -i inventory/dc01/hosts -K --ask-vault-pass --check

* Check ansible lint for syntax check
  * ansible-lint roles/freeipa_server_replica

