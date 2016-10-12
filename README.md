Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

Filter Chain: 


       - name: "Options"
         chain: "INPUT"  (supported values: INPUT/OUTPUT/FORWARD)
         ctstate: "RELATED,ESTABLISHED"
         jump: "DROP"  
         source: "10.0.1.1"
         to_source: "10.0.5.5"
         destination: "10.0.2.2" 
         to_destination: "10.0.5.5"
         protocol: "tcp"
         in_interface: "eth0"   (cannot be used with OUTPUT)
         out_interface: "eth0"  (cannot be used with INPUT)
         src_port: "80"
         dst_port: "80"
         
NAT Chain:

       - name: "Options" 
         chain: "PREROUTING"
         ctstate: "RELATED,ESTABLISHED"
         jump: "SNAT"
         source: "10.0.1.11"
         destination: "94.142.241.115" 
         protocol: "tcp"
         in_interface: "eth0"
         out_interface: "eth0"
         src_port: "80"
         dst_port: "80"

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).

