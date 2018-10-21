# ansible-traning

#### day1

```bash
# run test vm and add it into you ~/.ssh/config
vagrant up vm1
vagrant ssh-config 2>/dev/null | grep -A9 "^Host vm1" >> ~/.ssh/config

# check ansible connection (if does not work, check the day1/inventory file)
ansible vm1 -i day1/inventory -m ping

# generate ssh key for user1
ssh-keygen -q -N '' -C user1 -t rsa -f day1/files/id_rsa_user1

# run playbook
ansible-playbook day1/site.yml -i day1/inventory

# check new connection with new user, it's group and key in .ssh/authorized_keys
ssh user1@192.168.33.101 -i day1/files/id_rsa_user1

[user1@vm1 ~]$ groups
user1 wheel

[user1@vm1 ~]$ id
uid=2000(user1) gid=2000(user1) groups=2000(user1) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023

[user1@vm1 ~]$ ll .ssh/authorized_keys
-rw-------. 1 user1 user1 387 Oct 21 18:54 .ssh/authorized_keys

[user1@vm1 ~]$ sudo -s
[root@vm1 ~]#

```


create a password for ansible module
```
ansible all -i day1/inventory, -m debug -a "msg={{ 'password1' | password_hash('sha512')}}"
day1/inventory | SUCCESS => {
    "msg": "$6$SlQNmPB/ptavrX/q$xg1AKdkSnK1MgNSs7nd36K8TwHsiff215RmsJiKTA8pCAp7HezbX.TRyepA3BGLfW4gfTfw5KE3ZaiMMQsCOj0"
}
```