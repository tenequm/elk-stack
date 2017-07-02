ELK stack provisioning play.
===

This play establishes stack with 2 client computers (just to show it's work) and 1 ELK server, that aggregates and shows collected information. Also it configures firewall, so onlu needed ports will be opened.

Clients
===
Clients are provisioned on DigitalOcean droplets. `client-setup.yml` playbook doesn't have much variables, the only important one that should be declared is `api_token` more about this variable look in my another repository [ansible-digo](https://github.com/tenequm/ansible-digo). Also you should an RSA key pair into `ssh_keys` directory, so you will have more easier way to connect to your clients, as you will have keys to access it.
They also will have installed and configured `filebeat` apps and will send statistics to ELK server from scratch.

ELK Server
===
At first change the ip address of the ELK server host in `inventory` file, other way it wouldn't have any place where to apply provisioning.
It is fully provisioned with my [tenequm.elk](https://github.com/tenequm/elk) role, required variable is `elk_server_domain`, so don't forget to mention it when using this role.

Dependencies
------------
Don't forget to run `ansible-galaxy install -r requirments.yml` before start, so you would have all the needed dependencies.

License
-------
MIT

Author Information
------------------

This role was created in 2017 by [Mykhaylo Kolesnik](http://github.com/1nfinitum).
