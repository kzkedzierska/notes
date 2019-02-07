# Setting up the key verification for an ssh connection


## Prerequisites

**Required**
* ssh-keygen
* ssh-copy-id

**Helpful** - necessary to copy the key to github account. 
* xclip

```bash
sudo apt install ssh-keygen ssh-copy-id
```

## Creating a key

First, we need to create a key. We can do that by simply typing in ssh-keygen in our consol. This will result in 2048 bit RSA key. 

```bash
ssh-keygen
```

First we will be asked as to where to save the key?
```bash
~$ ssh-keygen 
Generating public/private rsa key pair.
Enter file in which to save the key (/home/username/.ssh/id_rsa): 
```

I keep my keys in the defualt directory, but like to name them as I use keys for multiple things (connecting to the server, github and more). Remebmer to pu the whole path for the key (or navigate to the directory you want to store your key), otherwise it will be saved in a current directory. 

Next, we are asked for passphrase. If you wish not to have a password protected key (i.e. don't want to prompted for a password every time you use it, just press enter). It is recommended though to encrypt the key so that it cannot be used by someone who shouldn't otherwise have access. For strong passwords I either use my [KeePassXC](https://keepassxc.org/) random generator or use one of the [online tools](https://passwordsgenerator.net/). 

```bash
~$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/username/.ssh/id_rsa): /home/username/.ssh/work_server
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/username/.ssh/work_server
Your public key has been saved in /home/username/.ssh/work_server.pub.
The key fingerprint is:
SHA256:sP/uJ20hblyGGlQGf4/iASWXU10cEUwdtVbjk8nbh0g username@yoga
The key's randomart image is:
+---[RSA 2048]----+
|        o.oo..oX@|
|         ==   +.O|
|      . .o..E  O |
|       o.. o +..+|
|      ..S o.o o.o|
|       ...oo+   .|
|        .=.= .   |
|        ..= +    |
|         +++     |
+----[SHA256]-----+
```

There is much more to the ssh-keygen program than what's described above, I definately recommend giving a manual a read! For example you may wish to increase the number of bits to 4048 by specifing it with `-b 4048`, or add a comment to the key with `-C "dell machine"`. You can access the info about the program by simply typing:

```bash
man ssh-keygen
```

## Copying the key to the server

Next, we want to copy the key to the server. This can be done by:

```bash
ssh-copy-id -i /home/username/.ssh/work_server userName@hostName
```

You'll be prompted for your password, same way you log into the server normally. 

Again, it's worth reading manual pages on ssh-copy-id as you may want to specify ssh options for example. 

```bash
man ssh-copy-id
```

## Testing the connection

To test the key type:

```bash
ssh -i /home/username/.ssh/work_server userName@hostName
```
If you only have one key you should be able to just connect via key verification method by simply typing.

```bash
ssh userName@hostName
```
But it may be better to keep the path to the key in the command and just create an alias in your .bashrc, .bash_profile or equivalent.

```bash
alias work_server='ssh -i /home/username/.ssh/work_server userName@hostName'
```

## Github

To copy akey to your github account, please refer to this really nice [help pages](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/).
