# Linux users

There can be multiple users in a linux. They can be grouped and allowed to perform only certain operations. This can be controlled using 
read/write/execute (stickybit) permission.

# List users

```
cat /etc/passwd
```

# Show single user
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


# Create new user
```
useradd <username> 
```

# Create password for the user

```
password <username>
```

# Create user with and assign home directory

```bash
useradd <username> -d <directory location>
```

# Assign directory to existing user

```bash
usermod -d <new-directory> <username>
```



