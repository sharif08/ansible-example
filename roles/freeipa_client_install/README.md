ROLE
=========

This role is used to install freeipa client

Role Variables
--------------

*    internal_freeipa_ldap_server_hostname: "{{ hostvars[groups.ldapserver[0]].host_fqdn }}"
*    internal_freeipa_ldap_server_ip: "{{ hostvars[groups.ldapserver[0]].host_ip }}"
*    internal_freeipa_ldap_server_replica_ip: "{{ hostvars[groups.ldapserver[1]].host_ip }}"
*    internal_freeipa_client_password: "{{ ldap_server.password }}"
*    internal_freeipa_client_fqdn: "{{ host_fqdn }}"
*    internal_freeipa_client_realm: "{{ host_domain }}"
*    internal_clinet_host_name:  "{{ host_name }}"


Dependencies
------------

* role: docker_install
* role: freeipa_prepare_client

License
-------
BSD


Playbook
--------

- hosts: ldap_clients
  remote_user: "{{ admin.user }}"
  gather_facts: no
  become: yes

  roles:
    - freeipa_client_install


- hosts: vie01-freeipa01.r3c.mgms
  remote_user: "{{ admin.user }}"
  gather_facts: no
  become: yes
  tasks:
    - command: docker exec -it "{{ base.docker.ldap_server.container_name }}-master1" bash -c "ipa service-add HTTP/{{ ipa_client_fqdn }}"

  vars:
    ipa_client_fqdn:                  #ipa_client_fqdn: vie01-bastion01.r3c.mgms


Syntax:
------
* How to run the freeipa Playbook, check the playbook file location first.
  * ansible-playbook playbooks/ldap_server/client_install.yml -i inventory/dc01/hosts -e ipa_client_fqdn=  -e ipa_client_ip= -K --ask-vaul-pass --check

* Check ansible lint for syntax check
  * ansible-lint roles/freeipa_client_install
