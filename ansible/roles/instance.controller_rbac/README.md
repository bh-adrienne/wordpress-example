instance.controller
=========

Configures the Kubernetes controller plane nodes.

Requirements
------------

- Must be an EC2 instances, as it uses the EC2 facts to get the current IP address.

Role Variables
--------------

- `env` - the Environment tag passed in. Used for identification/labeling.
- `token_csv` - username and password variable for configuring kubectl access.  Default values are provided and should NOT be used.  It is recommended to create an Ansible vault file with different credentials to override these.
- `volume_path` - the path to store the CFSSL files on.  Defaults to `/data`.
- `controller-ca.pem` - the public certificate of the CA that signs all controller instances.
- `{{ inventory_hostname }}.pem` - the instance public certificate.
- `{{ inventory_hostname }}-key.pem` - the instance private key.
- `service-account.pem` - the Kubernetes service account public certificate.
- `service-account-key.pem` - the Kubernetes service account private key.
- `etcdclient-ca.pem` - the etcd client CA.
- `etcdclient-key.pem` - the etcd client private key.
- `etcdclient.pem`- the etcd client public certificate.
- `node-ca.pem` - the public certificate of the CA that signs all node instances.

All SSL data is generated by the `instance.cfssl_kubernetes` Ansible role.

Dependencies
------------

- `instance.cfssl_kubernetes` - for SSL certificates.  

Example Playbook
----------------

N/A

License
-------

BSD

Author Information
------------------

Bill Cawthra 
