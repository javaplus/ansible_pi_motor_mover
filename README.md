
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

Set up hosts:

```

sudo vi /etc/ansible/hosts

```

Was having issues running ansible commands... it would not authenticate would get:
```
192.168.1.114 | UNREACHABLE! => {
    "changed": false,
    "msg": "Failed to connect to the host via ssh: Permission denied (publickey,password).\r\n",
    "unreachable": true
}
```

sudo apt-get install sshpass


Take 2... trying:

```
ssh-keygen -t rsa -C "pi"

 barry@DESKTOP-IEEFA0B:/mnt/f/workspaces/RaspberryPiImages/PiProjects/ansible_pi_motor_mover$ ssh-keygen -t rsa -C "pi"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/barry/.ssh/id_rsa):
/home/barry/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/barry/.ssh/id_rsa.
Your public key has been saved in /home/barry/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:HC8PlMwH2uJk5hhykvVY3HIvijx2OyZAKFMXugz/1Xo pi
The key's randomart image is:
+---[RSA 2048]----+
|    oo...        |
|  .+.+o=oo       |
|.o=.+ BoB..      |
|++.= O =.+.      |
|.o+...+.S..      |
|  ..=.o. +       |
|   o.o..E .      |
|    . +.         |
|     o .         |
+----[SHA256]-----+

 ssh-copy-id -i ~/.ssh/id_rsa.pub pi@192.168.1.114


ssh-copy-id -i ~/.ssh/id_rsa.pub pi@192.168.1.114
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/barry/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'pi@192.168.1.114'"
and check to make sure that only the key(s) you wanted were added.


```
updated /etc/ansible/hosts to look like

```

192.168.1.114 ansible_connection=ssh ansible_ssh_user=pi


```
Then it worked

