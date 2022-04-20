# ansible_practise

## Install
---
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
## Ansible Playbook?
---
* ex.
    - Create playbook.yml
    ```yml
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
