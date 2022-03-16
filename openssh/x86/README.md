> This repository contains code for systems running RAIDiator OS 4.x on a 
> x86_64 (Intel) CPU.

# OpenSSH 6.6p1

## Purpose
This package will update the OpenSSH server and Client on the ReadyNAS to 
version 6.6p1.
This version supports newer key exchange algorithms and has support for ssh keys
using the ED25519 format.

## Warranty
Everything provided here is provided "as is" with no guarantees expressed or implied.
Use at your own risk.

## Installation

### Through the ReadyNAS web interface (preferred)

**Note:** You'll most likely need to use Firefox

The preferred method of installation is through the web interface of the ReadyNAS.
This method will install all needed packages and also automatically restarts the SSH
server process.

**Note:** Although this looks like an add-on it **won't show up** in the list of
installed add-ons after installation. The reason for this is that only system 
packages are updated. There's no additional functionality that needs configuration
through the web interface.

### Using the command line via SSH

**Prerequisites:** 
* SSH access to the ReadyNAS mus be anbled for this to work. This can be done using the
  `EnableRootSSH` add-on. (see directory netgear_stuff)
* You need an SSH client to access the command line of your ReadyNAS
* If your SSH client is a modern one, use `ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 <ip of your NAS>

1) Copy the files from the `/debs` folder to the home directory of the `root` user on
   your ReadyNAS. Either use an SFTP client or a command similar to this on the command
   line:

   ``` bash
   scp -oKexAlgorithms=+diffie-hellman-group1-sha1 debs/*.deb root@<ip_of_your_readynas>:
   ````
   
1) Open an ssh session to your ReadyNAS as user `root`. The password is the same as the one
   you're using to access the admin web interface of your ReadyNAS. On the commandline you'd do:

   ``` bash
   ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 root@<ip_of_your_readynas>
   ```

1) Install the Debian packages:

   ```
   dpkg -i --force-all *.deb
   ```

1) Manually restart the SSH server:

   ```
   /etc/init.d/ssh restart
   ```

1) Test that you're still able to login (use a new terminal!)

   ```
   ssh root@<ip_of_your_readynas>
   ```

1) If everything works you're done!

#### Disclaimer
I'm not affiliated with NETGEAR Inc. in any way. I just happen to be a ReadyNAS user who likes
to build apps/add-ons for stuff I'm either using myself or deem interesting.

#### Donations

If you like my work, donations to https://paypal.me/readynasxtras are always welcome.

