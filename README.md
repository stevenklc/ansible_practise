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

* docker voloume
    * ```/var/jenkins_home```is Jenkins data


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

### loop
* with_items and item
```yml
- name: XXX
  apt:
    name: "{{ item }}"
    update_cache: yes
  with_items: 
    - apt-transport-https
    - ca-certificates
```

```yml
- name: xxx
  user: 
    name: "{{ item.name }}"
    state: present
    groups: "{{ item.groups }}"
  with_items:
    - { name: 'test1', groups: 'wheel' }
    - { name: 'test2', groups: 'root' }
```

## Demo
---
* Test Taiwan HIGH SPEED RAIL URL\*2
```sehll ansible-playbook playbook_rule_url.yml ```
