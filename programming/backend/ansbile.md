## Install Ansible

- macos `brew install ansible`
- debian `sudo apt install ansible`
- pip `python3 -m pip install ansible`


## Ansible vault
```sh
ansible-vault create secret.yml

# password format
password: "asdf"

ansible-vault edit secret.yml
```

## Run playbook
```sh
# -K for sudo password
ansible-playbook run.yml -K --ask-vault-pass
```

## Ad hoc
### Ping
```sh
ansible all -m ping
```

### Get machine info
```sh
ansible all -m setup
```

### Run command
```sh
ansible all -a "df -h"

# similar to command but runs through /bin/sh
ansible all -m shell -a "df -h"
```

### Copy file
```sh
# -b become sudo
ansible all -m copy -a "src=./main.py dest=/home/lx mode=777" -b
```

### Delete file
```sh
ansible all -m file -a "path=/home/lx/main.py state=absent" -b
```

### Download from web to servers
```sh
ansible all -m get_url -a "url=https://github.com/lxhan/test dest=/home/lx" -b
```

### Debug
```sh
ansible all -a "df -h" -vvvvv
```

## Playbook

### Install with snap
```sh
- name: install docker
  community.general.snap:
    name: docker
```

## Links

- [My Ansible playbook](https://github.com/lxhan/ansible)
