haproxy-ansible
===============

A simple haproxy 1.5 ansible playbook example with ssl termination. This will install the latest haproxy 1.5 from the nilya ppa, enable it, install a default config file and allow for ssl termination without the use of any additional software.

This has been tested on a Canonical provided Ubuntu 12.10 image in AWS.

How To Use
==========

```
git clone git@github.com:invokemedia/haproxy-ansible.git
```

* Add your hostname you wish to deploy to into the provided hosts file (replacing the default proxy.example.com)
* Replace the user/www_url/api_url values in the provided hosts file with valid values
* (Optional) Add your own backend servers and frontend rules to the haproxy-config file. Obviously you'll want to route traffic how and where you like. 
* (Optional) For SSL you'll need to have your own pem file created in the root with the file name certificate.pem

Assuming you have ansible installed you just need to run `ansible-playbook` with the supplied hosts file and playbook and it will install haproxy and the config file to the server for you.

```
ansible-playbook -i hosts main.yml
```

More Info
=========

You can setup multiple inventory files with different values for each, for example a dev/stage/prod file with different user/backend urls. Just replace the `hosts` file in the `ansible-playbook` command with the name of the correct file.

You'll certainly want to make the necessary adjustments to the haproxy config, it's a pretty barebones default setup. Example, the stats has no password oranything to block people from snooping on your data.

You can certainly take out the ssl if not necessary or make the routing operate as necessary for your application, this is just a simple example to get you started.
