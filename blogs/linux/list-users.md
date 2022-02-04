# Linux users

There can be multiple users in a linux. They can be grouped and allowed to perform only certain operations. This can be controlled using 
read/write/execute (stickybit) permission.

To check existing users

```
cat /etc/passwd
```

```
# getent passwd | grep vagrant
vagrant:x:1000:1000::/home/vagrant:/bin/bash
```
`getent` is like a database reader. It can read databases from `/etc` directory. 

The above command has printed a row containing seven columns explained below
1. login name
2. `x` represents encrypted password
3. userid (uid)
4. groupid 
5. user's name or comment field
6. home directory of the user
7. login shell
