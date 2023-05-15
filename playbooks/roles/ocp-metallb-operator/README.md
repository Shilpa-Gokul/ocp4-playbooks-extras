ocp-metallb-operator
=========

This role is used to deploy Kubernetes MetalLB Operator and run e2e tests.

Requirements
------------

- OCP 4.x healthy cluster on PowerVS.
- OCP secret with name ***podman-secret*** in the default namespace which is used for global secret update and has following keys:
   ***username***, ***password*** and ***registry***

Role Variables
--------------

| Variable                    | Required | Default                                           | Comments                                                                                                                       |
|-----------------------------|----------|---------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| metallb_enabled             | no       | false                                             | Set it to true to run this playbook                                                                                            |
| metallb_install_operator    | no       | true                                              | Set it to true to install the Kubernetes MetalLB Operator                                                                      |
| metallb_catalogsource_image | no       | ""                                                | Custom catalog source index image for MetalLB Operator. If not defined, default `redhat-operators` catalog source will be used |
| metallb_upgrade_channel     | no       | stable                                            | Operator upgrade channel                                                                                                       |
| metallb_directory           | no       | `/tmp/metallb`                                    | Working directory for MetalLB Operator                                                                                         |
| metallb_golang_tarball      | no       | https://go.dev/dl/go1.18.6.linux-ppc64le.tar.gz   | HTTPS URL for golang tarball                                                                                                   |
| metallb_e2e                 | no       | false                                             | Set it to true to run e2e                                                                                                      |
| metallb_e2e_git_repository  | no       | https://github.com/openshift/metallb-operator.git | Git respository for e2e tests                                                                                                  |
| metallb_git_branch          | no       | main                                              | Git branch for e2e                                                                                                             |
| metallb_cleanup             | no       | true                                              | Flag is used to clean metallb Operator resources                                                                               |

Dependencies
------------

- None

Example Playbook
----------------
```
---
- name: Installation of the MetalLB Operator and run e2e
  hosts: bastion
  tasks:
  - name: Deploy MetalLB Operator
    include_role:
      name: ocp-metallb-operator
```

License
-------

See LICENCE.txt

Author Information
------------------

shilpa.gokul@ibm.com
