# System Collector
ansible-playbook utility to gather system informations on hosts including:

* installed packages
* firewall rules
* open ports
* connected networks
* routing tables
* running services
* system logs

## Usage

0. Install ansible and clone the repo
```
$ pip install ansible
$ git clone <REPO>
```

1. Describe the hosts you want to analyze in the `hosts` file:
```
<HOSTNAME>	ansible_host=<IP>	ansible_user=<USERNAME>
```
2. Fill the `host_vars` directory with a file for each host, named as `<HOSTNAME>`, you will place host passwords there (related to the username you specified in the `hosts` file), in the form of:
```
ansible_become_pass: <PASSWORD>
```
3. [OPTIONAL BUT RECOMMENDED] Encrypt each password file to not leave them in plaintext:
```
ansible-vault encrypt [PASSWORD_FILE]
```
for each file in `host_vars`.

`ansible-vault` will ask for a master password, once set, execute the playbook using `--ask-vault-pass`.

4. Run using:
```
ansible-playbook -i hosts collect.yml --ask-vault-pass
```
You will obtain the output in `output/<HOSTNAME>`


