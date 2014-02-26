A repo of ansible playbooks for me to learn ansible better with. So far, it doesn't seem
like you buy a lot by using ansible to do the initial provision (the glue code doesn't really 
add any features I didn't have using nova or supernova, and I don't mind running an ansible
playbook as a 2nd command after that).

This playbook.yml does the following:
- add user 'martin' with various defaults
- add public ssh key for 'martin' to login without a password


To boot a new instance:
```
$ snr boot chat.rax.mbs3.org --image 2ab974de-9fe5-4f5b-9d58-766a59f3de61  --flavor performance1-1 --key-name cloudhosts --poll
```

For non-dynamic inventory, run following command after arranging inventory to your liking (see examples, non-trivial unless DNS exists):
```
$ ansible-playbook playbook.yml -i inventory/inventory -vvvv
```

For dynamic inventory, run:
```
$ RAX_CREDS_FILE=~/.raxpub ansible-playbook playbook.yml -i inventory/rax.py -vvvv
```

Layout follows http://docs.ansible.com/playbooks_best_practices.html#directory-layout.
