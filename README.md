# testbed 

This is a simple Vagrantfile used to generate one or more virtual machines to use as a target environment for testing. An example use case would be to point a provisioner at these machines and test a deploy process (as opposed to using the built-in provisioning that Vagrant provides). 

## Usage

The vagrant profile is controlled by the following environment variable settings:

* **BOXES** - The number of boxes to generate. Defaults to 1.
* **IP_START** - The starting point for the range of IPs to use. This is only last octet of an IP Address, which will be the first IP in a range of IPs generated. Defaults to 70, which will assign IPs to machines starting at 192.168.33.70.

### Examples

Create one machine with IP ```192.168.33.70```
```
vagrant up
```

Create two machines with IPs ```192.168.33.70``` and ```192.168.33.71```

```
BOXES=2 vagrant up
```

Create two machines with IPs ```192.168.33.40``` and ```192.168.33.41```
```
BOXES=2 IP_START=40 vagrant up
```

### Caveats

The environment variables must be used for all subsequent operations, such as vagrant SSH. For this reason, it is recommended to just export those variables to your environment vs using them on a per command basis. 

The following example would not work correctly without the environment variables:

```
BOXES=2 IP_START=40 vagrant ssh box2
```

