1. ## Creating and Deleting Users in Linux

In Linux, creating and deleting users can be done using commands such as `useradd`, `userdel`, and checking user details with the `id` or `cat` `/etc/passwd` command.

**Creating a User**
To create a new user on your system, you can use either of the following commands:

1. `useradd` Command:

```bash
useradd username
```

2. `adduser` Command (more user-friendly):

In some Linux distributions (like Debian-based systems), adduser is a more user-friendly script for creating users.

```bash
adduser username
```

Explanation:
username → This is the name of the user you want to create.
Both commands create a new user, but adduser is typically more interactive and sets up additional configuration like password and home directory automatically.
