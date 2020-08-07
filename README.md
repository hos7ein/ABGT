ABGT
----

### Introduction ###

`ABGT` is not that ABGT! It is Ansible Blue Green Task which we can use it for preparing hosts, building docker images and Blue/Green deployment.


### Preparing hosts ###

To prepare hosts you can use 1-Ansible_playbook-host-configuration playbook. This playbook include a few task for installing some necessary packages and deploy HAProxy load balancer. After clone ABGT project, change your current path:

```$ cd ABGT/1-Ansible_playbook-host-configuration```

Then open `inventory` file and put your hosts information into this file:

```$ vi inventory```

Now for deploying the playbook you should run the beneath command:

```$ ansible-playbook -i inventory main-playbook.yml```

### Build docker images ###

To Build docker images you can use 2-Ansible_playbook-build playbook. Change your current path:

```$ cd ABGT/2-Ansible_playbook-build```

Then open `inventory.ini` file and put information of your build host into this file:

```$ vi inventory.ini```

Since we need to login to Docker registry, we need to be able to put our secrets in the code. To avoid exposing credentials in the clear, we will use ansible-vault to encrypt them.

```$ vi secrets.yml```

Run ansible-vault against the file. It will prompt for a password to encrypt it:

```$ ansible-vault encrypt secrets.yml```

Now for deploying the playbook you should run the beneath command:

```$ ansible-playbook -i inventory.ini  build.yml --ask-vault-pass```


### Blue/Green deployment ###

To Blue/Green deployment you can use the 3-Ansible_playbook-deploy playbook. This folder include 3 files for blue/green deployment app and rollback. First of all change your current path:

```$ cd ABGT/3-Ansible_playbook-deploy```

Then open `inventory.ini` file and put your hosts information into this file:

```$ vi inventory.ini```

You can now use the appropriate file according to your needs, but before using them, you need to put the required information into the variables.


To blue deployment app:

```$ ansible-playbook -i inventory.ini 1-B-deploy.yml```


To green deployment app:

```$ ansible-playbook -i inventory.ini 2-G-deploy.yml```

To rollback:

```$ ansible-playbook -i inventory.ini rollback.yml```









## Contact

**Project website**: https://github.com/hos7ein/ABGT

**Personal website**: https://fedorafans.com

**Author**: Hossein Aghaie <hossein.a97@gmail.com>

**Twitter**: Hossein Aghaie [@hos7ein](https://twitter.com/hos7ein)


## License

ABGT source code is available under the GPL-3.0 [License](/LICENSE).
