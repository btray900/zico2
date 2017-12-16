# zico2
boot2root vm walkthrough


## netdiscover

netdiscover finds us the VM IP: 192.168.56.104
kali ip: 192.168.56.103

![Alt text](./netdiscover.png?raw=true)


## nmap

nmap shows what is available for tcp

![Alt text](./nmap.png?raw=true)


## browse

browsing the webste leads us to an LFI candidate

![Alt text](./lficheck.png?raw=true)


## lfi

LFI was successful. SSH with cracked credentials from below was unsuccessful for me

![Alt text](./burplfi.png?raw=true)


# dirb

dirb found the directory 'dbadmin' with phpLiteAdmin/1.9.3 web app. Default password works

![Alt text](./phplogin.png?raw=true)


webapp users

![Alt text](./users.png?raw=true)


# poc

Google for the web app gives us a PoC

![Alt text](./poc.png?raw=true)


php is crafted for injection

![Alt text](./phpinject.png?raw=true)


visit the db page, you should see a web log hit on your attacker

![Alt text](./burp2.png?raw=true)


# low-level shell

poc returns a low-level shell

![Alt text](./lowshell.png?raw=true)


# enumerate

interpreters and compilers available

![Alt text](./compiler.png?raw=true)


os version

![Alt text](./os-enum.png?raw=true)


# kernel exploit

Google sends us to a candidate. The targets are slightly different than our kernel but worth a shot for quick escalation

![Alt text](./kernel-exploit.png?raw=true)


# root 1

Upgrading the shell to tty allows successful exploitation. But this is not in the spirit of the VM where enumeration is more challenging to find a way for escalation

![Alt text](./kernel-root.png?raw=true)


## enumeratino - method 2

Compromise a password in wordpress config

![Alt text](./wp-config.png?raw=true)


## ssh

SSH as zico with compromised credentials gives a low-level shell

![Alt text](./ssh.png?raw=true)


# sudo

sudo -l (el) lists sudo commands we can run

![Alt text](./sudol.png?raw=true)


# fu

Searching the web describes how to run arbitrary code with tar

![Alt text](./google-tar.png?raw=true)


# maliscious command

compile a malicious binary

![Alt text](./pwnc.png?raw=true)


# exploit for root

<html><pre>
\(*_*)
  ( (>
  /  \
</pre></html>
  
  
sudo tar ftw
  
![Alt text](./tar-ftw.png?raw=true)
  

# ctf

![Alt text](./flag2.png?raw=true)


# thanks

thanks to rafael for the vm



