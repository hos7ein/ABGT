ABGT
----

### Introduction ###

`ABGT` is not that ABGT! It is Ansible Blue Green Task which we can use it for preparing hosts, building docker images and Blue/Green deployment. 


### Preparing hosts ###

To prepare hosts you can use 1-Ansible_playbook-host-configuration playbook. This playbook include a few task for installing some necessary packages and deploy HAProxy load balancer. After clone ABGT project, change your current path:

```cd ABGT/1-Ansible_playbook-host-configuration```

Then open `inventory` file and put your hosts information into this file:

```vi inventory```

Now for deploying the playbook you should run the beneath command:

```ansible-playbook -i inventory main-playbook.yml```

### Build docker images ###

To Build docker images you can use 2-Ansible_playbook-build playbook. Change your current path:

```cd ABGT/2-Ansible_playbook-build```

Then open `inventory.ini` file and put information of your build host into this file:

```vi inventory.ini```

To push docker images to docker hub you should enter your docker hub information into `secrets.yml` file:

```vi secrets.yml```

Because of this information is sensitive we should encrypt this file. 










## Contact

**Project website**: https://github.com/hos7ein/ABGT

**Personal website**: https://fedorafans.com

**Author**: Hossein Aghaie <hossein.a97@gmail.com>

**Twitter**: Hossein Aghaie [@hos7ein](https://twitter.com/hos7ein)


## License

FireLEMP source code is available under the GPL-3.0 [License](/LICENSE).
