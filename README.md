# Epicodus software deployment

1. `brew install ansible19`
1. `brew install https://raw.githubusercontent.com/kadwanev/bigboybrew/master/Library/Formula/sshpass.rb`
1. `git clone https://github.com/epicodus/ansible_deployment`
1. In the **ansible_deployment** root, create a **group_vars** directory with an **all** file and add the following (make sure to update the key and passwords):

    ```
    ansible_connection: ssh
    ansible_ssh_user: epicodus
    ansible_ssh_pass: whatever_ssh_password
    ansible_sudo_pass: whatever_sudo_password
    sketch_key: whatever_sketch_key
    ```

1. create a **~/.ansible.cfg** file and add the following (make sure to update the inventory path):

  ```
  [defaults]
  inventory = whatever/path/to/ansible_deployment/hosts

  [ssh_connection]
  pipelining=True
  ```

1. `ssh epicodus@whatever_remote_computer_ip` and type `yes`
  - if you get an error, then the remote computer key already exists in **~/.ssh/known_hosts**; remove it from **known_hosts** and try again
1. `cd ansible_deployment`
1. `ansible-playbook site.yml`
