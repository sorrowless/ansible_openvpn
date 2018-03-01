Role Name
=========

Role to install and configure OpenVPN server

#### Requirements

Ansible 2.4

#### Role Variables

```
server_name - filename for target server keypair file. It can be useful in case
  you already had some OpenVPN PKI and now just want to migrate to the new
  version, so if you had OpenVPN server keys named after 'some.name.[key,crt]'
  and will set server_name var to 'some.name', your keys won't be regenerated
  and you will continue to use old ones.
real_server_name - hostname which clients should connect to. In case you will
  use it, exactly that name will be shown in client ovpn file as server to
  connect to, otherwise 'server_name' var will be used. Optional.
additional_pushes - list of additional pushed which will be advertised for
  clients. Optional.
clients - list of clients to issue certificate for. In case of first-time
  installation it will be ignored due to way revokation list created. Next
  times it will be used as a name of client to create certificate for.
```

#### Dependencies

None

#### Example Playbook

```yaml
    - name: Install VPN server and create some client certs for it
      hosts: vpn-server
      remote_user: root
      sudo: yes
      vars_prompt:
        - name: "clients"
          prompt: "Please enter login name"
          private: no
      roles:
        - vpn
```

#### License

Apache 2.0

#### Author Information

Stanislaw Bogatkin (sbog@sbog.ru)
