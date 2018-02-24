
#Setting up SSH keys
```
barry@DESKTOP-IEEFA0B:~$ ssh-keygen -t rsa -b 4096 -C "btarlton@gmail.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/barry/.ssh/id_rsa):
Created directory '/home/barry/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/barry/.ssh/id_rsa.
Your public key has been saved in /home/barry/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:3KGuc7MPEbgM/n2d2wwS/97FBN6R3ePrBRGCARs9hgA btarlton@gmail.com
The key's randomart image is:
+---[RSA 4096]----+
|    E...o+.o. .  |
|       ..o=  . .+|
|    . . o...  o+o|
|   . o o + . ..+o|
|    . o S o   o.o|
|     . o . + . +.|
|      . + o =  .+|
|      ..oo . *..o|
|      .o.+. ..=..|
+----[SHA256]-----+
barry@DESKTOP-IEEFA0B:~$

```
Add ssh-key

```
barry@DESKTOP-IEEFA0B:~$ ssh-copy-id -i ~/.ssh/id_rsa.pub pi@192.168.1.114
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/barry/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
pi@192.168.1.114's password:

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'pi@192.168.1.114'"
and check to make sure that only the key(s) you wanted were added.

```

