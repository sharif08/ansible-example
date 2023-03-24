Role Name
=========
This role is used to install basic required packages for all hosts



Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:


- hosts: cockpit_client
  remote_user: "{{ admin.user }}"
  gather_facts: no
  become: yes


  roles:
    - basic_installation

License
-------

BSD

Syntax:
------
* How to run the freeipa Playbook, check the playbook file location first.
  * ansible-playbook playbooks/basic-install/all-host.yml -i inventory/dc01/hosts -K --ask-vaul-pass --check

* Check ansible lint for syntax check
  * ansible-lint roles/basic_installation

