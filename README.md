# Ansible playbook for managing linux users

  Basic add/remove functionality.
  All users will be asked for password change at first login.

## Usage:

  - Create sample inventory and provide `users` variable:

    Example:
    ```
      development:
        hosts:
          - dev-master-srv
          - dev-slave-srv
        vars:
          password: 'myPassword'
          ansible_user: ansible
          ansible_become_pass: 'pass'
          users:
            - { name: 'daenerys_t', groups: 'developers,wheel' }
            - { name: 'eddard_s', remove: yes }
    ```

  - Place public keys for users at `./public_keys` folder:

        ./public_keys/daenerys_t.pub

  - Run Ansible playbook

        ansible-playbook ./users.yml