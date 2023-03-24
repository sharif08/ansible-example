Role Name
=========

This role is used to create rancher docker container for k8s cluster


Role Variables
--------------

*    internal_client_crts_dir: "{{ base.ipa_client.crts_dir }}"
*    internal_rancher_server_docker_name: "{{ base.docker.rancher.container.name }}"
*    internal_rancher_server_image: "{{ base.docker.rancher.container.image }}"
*    internal_rancher_server_tag: "{{ base.docker.rancher.container.tag }}"
*    internal_rancher_server_port1: "{{ base.docker.rancher.container.port1 }}"
*    internal_rancher_server_port2: "{{ base.docker.rancher.container.port2 }}"
*    internal_rancher_server_port3: "{{ base.docker.rancher.container.port3 }}"
*    internal_rancher_server_port4: "{{ base.docker.rancher.container.port4 }}"
*    internal_rancher_server_home_dir: "{{ base.docker.rancher.home_dir }}"


Dependencies
------------
- roles: docker_install


License
-------

BSD

Playbook
--------

cat playbooks/kubernetes/rancher_install.yml 

- hosts: deployment_server
  remote_user: "{{ admin.user }}"
  gather_facts: no
  become: yes

  roles:
    - rancher_install

Syntax-Check
------------

* ansible-playbook  playbooks/kubernetes/rancher_install.yml -i inventory/vie01-dc01/hosts -K --ask-vault-pass --check

