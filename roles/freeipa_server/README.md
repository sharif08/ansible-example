Role Name
=========

This role is used to install freeipa server(ldap server), check CA Certificate:<host_ip or HostName>/ipa/config/ca.crt

Role Variables
--------------

*    internal_ldap_server_master01_domain: "{{ hostvars[groups.ldapserver[0]].host_domain }}"
*    internal_ldap_server_master01_ip: "{{ hostvars[groups.ldapserver[0]].host_ip }}"
*    internal_ldap_server_master01_dns: "{{ hostvars[groups.ldapserver[0]].ldap_server_dns }}"
*    internal_host_user: "{{ admin.user }}"
*    internal_ldap_client_ip: "{{ hostvars[groups.deployment_server[0]].host_ip }}"
*    internal_ldap_server_docker_name: "{{ hostvars[groups.ldapserver[0]].base.docker.ldap_server.container_name }}"
*    internal_ldap_server_docker_image: "{{ hostvars[groups.ldapserver[0]].base.docker.ldap_server.image }}"
*    internal_ldap_server_docker_tag: "{{ hostvars[groups.ldapserver[0]].base.docker.ldap_server.tag }}"
*    internal_docker_restart_policy: "{{ hostvars[groups.ldapserver[0]].base.docker.restart_policy }}"
*    internal_ldap_server_admin_pass: "{{ ldap_server.password }}"


Dependencies
------------

* role: docker_install

License
-------

BSD

Syntax:
------
* How to run the freeipa Playbook, check the playbook file location first.
  * ansible-playbook playbooks/ldap_server/ldap_master_install.yml -i inventory/dc01/hosts -K --ask-vaul-pass --check

* Check ansible lint for syntax check
  * ansible-lint roles/freeipa_server
