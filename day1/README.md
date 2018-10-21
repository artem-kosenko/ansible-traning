# ansible-traning - day1

## HOMEWORK ##

Develop a Playbook for creating a user on remote system (Linux).
Consider using following variables (if they are really needed):
- user_name
- user_id
- user_primary_group
- user_primary_group_id
- user_password
- user_authorized_key
- user_home_dir
Configure sudoers privileges, disable requiretty (with template modue)
Use privilege escalations where it’s required


Playbook’s skeleton:
```yaml
- hosts: all

  vars:
    user_name:
    user_id:
    user_primary_group:
    user_primary_group_id:
    user_password:
    user_authorized_key:
    user_home_dir:

  tasks:
  ...

```


Please consider following questions:
a) Is your playbook idempotent?
b) Provide an example of playbook’s convergent behavior.
c) How can you make sure that your playbook follows an idea of Congruent Infrastructure?
