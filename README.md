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
