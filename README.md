# Ansible role icinga-cluster

Ansible role to set-up icinga2 cluster

## Requirements

Certificates stored in `filed` directory

## Example Playbook

```yaml
- hosts: icinga2-master,icinga2-satellites
  roles:
   - role: icinga2-cluster
     icinga2_cluster_endpoints:
          master.example.org: {}
          node-1.example.org: {}
          node-2.example.org: {}

     icinga2_cluster_zones:
            master:
               endpoints: [ 'master.example.org' ]
            node-1:
               endpoints: [ 'node-1.example.org' ]
               parent: 'master'
            node-2:
               endpoints: [ 'node-2.example.org' ]
               parent: 'master'

     icinga_cluster_identity: '{{ ansible_hostname }}'
```

## Role Variables

See `defaults/main.yml`

## License

BSD 3 || WTFPL

## Author Information

Veros Kaplan < https://github.com/VerosK/ansible-icinga2-cluster >