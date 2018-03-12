# Kubernates the hardway using Vagrant

This is a vagrant project that follows this guide: [Kubernates The Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way) but using [Vagrant](https://www.vagrantup.com/) instead of [Google Cloud Engine](https://cloud.google.com/compute/?hl=es). 

This is not code to run on production environment, but it can help to understand the steps involved into configuring a Kubernates cluster.

## Prerequisites

You need to have [Vagrant](https://www.vagrantup.com/) installed in your machine.

Also, you need to create the following folders:

```
$ mkdir shared
$ mkdir ssh_keys
```

Inside the ssh_keys folder, generate a ssh key of type ed25519. Using Linux, Mac OS X or Cygwin in Windows:

```
$ mkdir ssh_keys
$ cd ssh_keys/
$ ssh-keygen -t ed25519 -f id_ed25519
```

## The environment

By default this generates 5 VMs, you can change the number of worker and controller nodes just editing this two variables of the Vagrantfile:

```Ruby
total_mumber_of_controllers = 2
total_number_of_workers = 2
```

The schema is the following one. A client/load balance machine is going to be created with ip address: 10.0.0.100. Then several controllers, to a maximum of 9, controller-1 will have ip address 10.0.0.51, controller-2 will have ip address 10.0.0.52, and so on. Finally, a maximum of 49 worker nodes can be created, worker-1 will have ip address 10.0.0.1, worker-2 will have ip address 10.0.0.2 and so on.

You can ssh to any of this VMs using the hostname, for example:

```
vagrant ssh controller-3
```