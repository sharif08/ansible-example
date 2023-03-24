Role Name
=========

This role is used to create New Certificates for Ipa Clients

Role Variables
--------------

*    internal_ldap_server_master01_ip: "{{ hostvars[groups.ldapserver[0]].host_ip }}"
*    internal_ldap_server_admin_pass: "{{ ldap_server.password }}"
*    insternal_host_service_fqdn: "{{ host_service_fqdn }}"
*    internal_alias_host_service_fqdn: "{{ alias_host_service_fqdn }}"
*    internal_host_user: "{{ admin.user }}"
*    internal_ldap_client_ip: "{{ hostvars[host_service_fqdn].host_ip }}"
*    internal_client_crts_dir: "{{ base.ipa_client.crts_dir }}"
*    internal_ldap_domain: "{{ hostvars[host_service_fqdn].host_domain }}"
*    internal_ldap_server_docker_name: "{{ hostvars[groups.ldapserver[0]].base.docker.ldap_server.container_name }}"



Example Playbook
----------------

- hosts: ldapserver
  remote_user: "{{ admin.user }}"
  gather_facts: no
  become: yes

  roles:
    - certs_ipa_hosts

  vars:
    host_service_fqdn:                 # host_service_fqdn: vie01-bastion01.r3c.mgms  provide host name
    alias_host_service_fqdn:                   # alies_host_service_fqdn: project1.r3c.mgms   provide alies name



License
-------

BSD

Syntax:
------
* How to run the Certificate Playbook, check the playbook file location first.
  * ansible-playbook playbooks/certificate/alies_cert.yml -i inventory/dc01/hosts -e host_service_fqdn=  -e alias_host_service_fqdn= -K --ask-vaul-pass --check

* Check ansible lint for syntax check
  * ansible-lint roles/certs_ipa_hosts
