Scripts to create transfer server infrastructures for handing over
software artefacts from a vendor to an operator.

Architecture
------------

```
                            +
                            |
                            |       +--------------+
                            |       |              |
                            +-------+  transfer A  |
                            |       |              |
                            |       +--------------+
                            |
                            |
                            |       +--------------+
    +------------+          |       |              |
    |            |          +-------+  transfer B  |
    |  jumphost  +----------+       |              |
    |            |          |       +--------------+
    +------------+          |
                            |
                            |       +--------------+
                            |       |              |
                            +-------+  transfer C  |
                            |       |              |
                            |       +--------------+
                            +

```

Scripts
-------

**1. add_partner.yml**

Example:

> ./add_partner.yml  -e @partner.yml

An ansible playbook which creates a partner user account on the jumphost and configures a transfer server to allow for scp and git access.

The parameter file should provide following information:

```
# define ip address of the transfer server
transfer: "172.31.1.106"

# define user account
partner: "partner"

# define email of user
email: "admin@acme.com"

# define key of user
key: "ssh-rsa AAAAB..."
```

**2. del_partner.yml**

Example:

> ./del_partner.yml  -e @partner.yml

An ansible playbook which deletes a partner user account from the jumphost and removes any configuration on a transfer server allowing for scp and git access.

The parameter file should provide following information:

```
# define ip address of the transfer server
transfer: "172.31.1.106"

# define user account
partner: "partner"

# define email of user
email: "admin@acme.com"

# define key of user
key: "ssh-rsa AAAAB..."
```
