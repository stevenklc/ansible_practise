# ansible_practise

## Install
---
### Ansible
* Ubuntu
    ```shell
    sudo apt-get install software-properties-common
    sudo apt-add-repository ppa:ansible/ansible
    sudo apt-get update
    sudo apt-get install ansible
    ```
* Ansible-lint
    * install pip3
    ```shell
    sudo apt install python3-pip
    ```
    * install Ansible-lint
    ```shell
    pip3 install "ansible-lint"
    ```
    * add Path
    * Usage
    ```shell
    ansible-lint {name}.yml
    ```
### Jenkins
* Run
```shell
docker-compose up -d
```


## Ansible Playbook?
---
* ex.
    - Create playbook.yml
    ```yaml
    - hosts: server
      tasks: 
        # task 1
        - name: test connection
          ping:
          register: message

        # task 2
        - name: print debug message
          debug: 
            msg: "{{ message  }}"
    ```
## Usage
---
* roles
```shell
mkdir -p ./roles/{tasks_name}/tasks && touch ./roles/{tasks_name}/tasks/main.yml
```


* ex.main.yml
```yaml
- name: Install curl
  apt:
    name: curl
    # apt update
    update_cache: yes
```

* ex.playbook.yml
```yaml
- hosts: server
    roles:
      - { role: curl, become: yes }
```


* ansible.cfg
```shell
touch ./ansible.cfg
```

* ex.ansible.cfg  
```
[defaults]
roles_path = ./roles
inventory = ./inventory
private_key_file = ./private_key
```
