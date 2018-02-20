Role Name
=========

Role to install and configure OpenVPN server

Requirements
------------

Ansible 2.4

Role Variables
--------------

server_name - filename for target server keypair file. It can be useful in case
  you already had some OpenVPN PKI and now just want to migrate to the new
  version
real_server_name - hostname which clients should connect to
additional_pushes - list of additional pushed which will be advertised for
  clients

Dependencies
------------

None

Example Playbook
----------------

    - name: Install VPN server and create some client certs for it
      hosts: vpn-server
      remote_user: root
      sudo: yes
      vars_prompt:
        - name: "clients"
          prompt: "Please enter login name"
          private: no
        - name: "fullname"
          prompt: "Please enter full name"
          private: no
        - name: "mail"
          prompt: "Please enter email"
          private: no
      roles:
        - vpn


License
-------

Apache

Author Information
------------------

Stanislaw Bogatkin (sbog@sbog.ru)
