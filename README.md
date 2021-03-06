# Ansible role icinga-cluster

Ansible role to set-up icinga2 cluster config.
Requires already setup ansible

## Example Playbook

```yaml
- hosts: icinga2-master,icinga2-satellites
  vars:
     icinga2_cluster_endpoints:
          master.example.org: {}
          node-1.example.org: {}
          node-2.example.org: 
              address: "192.168.13.1"     # specify API  address when needed

     icinga2_cluster_zones:
            master:
               endpoints: [ 'master.example.org' ]
            node-1:
               endpoints: [ 'node-1.example.org' ]
               parent: 'master'
            node-2:
               endpoints: [ 'node-2.example.org' ]
               parent: 'master'
               
     # name of my icinga
     icinga_cluster_identity: '{{ ansible_hostname }}'
     
  roles:
   - role: icinga2-cluster

```

## Role Variables

See `defaults/main.yml`

## License

BSD 3 || WTFPL

## Author Information

[Veros Kaplan]

Module sponsored by [Moravian Library]


[Moravian Library]: http://mzk.cz/
[Veros Kaplan]: https://github.com/verosk/