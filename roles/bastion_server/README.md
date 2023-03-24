Role Name
=========
This Role is to configure Deployment Main Host (Bastion01)


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

- hosts: vie01-bastion01.r3c.mgms
  remote_user: "{{ admin.user }}"
  gather_facts: no
  become: yes

  roles:
    - bastion_server
    - helm_museum_install


License
-------

BSD

Syntax:
------
* How to run the freeipa Playbook, check the playbook file location first.
  * ansible-playbook playbooks/basic-install/bastion-host.yml -i inventory/dc01/hosts -K --ask-vaul-pass --check

* Check ansible lint for syntax check
  * ansible-lint roles/basic-installation

