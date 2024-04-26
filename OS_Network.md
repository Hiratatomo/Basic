# OS (Linux) Network  

1. [Secure Shell (SSH)](#ssh)
2. [Shell Command](#command)
3. [Network Communication](#network)
4. [Standard Input Standard Output](#intputoutput)
5. [Reference](#reference)
6. [Learning](#learning)

<a id="ssh"></a>  

### **1. ssh**  

> SSH, also known as Secure Shell or Secure Socket Shell, is a network protocol that gives users, particularly system administrators, a secure way to access a computer over an unsecured network.  
[https://www.techtarget.com/searchsecurity/definition/Secure-Shell](https://www.techtarget.com/searchsecurity/definition/Secure-Shell)  


The most basic use of SSH is to connect to a remote host for a terminal session. The form of that command is the following:
Example:  
```ssh UserName@SSHserver.example.com```  

```$ ssh -i ~/.ssh/training-2024-username.pem username@52.194.188.6```


This command will cause the client to attempt to connect to the server named server.example.com, using the user ID UserName. If this is the first time negotiating a connection between the local host and the server, the user will be prompted with the remote host's public key fingerprint and prompted to connect, despite there having been no prior connection:  

```
The authenticity of host 'sample.ssh.com' cannot be established.
 DSA key fingerprint is 01:23:45:67:89:ab:cd:ef:ff:fe:dc:ba:98:76:54:32:10.
 Are you sure you want to continue connecting (yes/no)?
```


<a id="command"></a>  

### **2. Shell Command**  

- 2-1. [Using 'vim' to create and edit a file](#create)
- 2-2.[Changing the name of a file](#change)
- 2-3.[Using the chmod command with sudo](#sudo)

<a id="create"></a>  

**2-1. Using 'vim' to create and edit a file**

1. Log into your server via [SSH](https://help.dreamhost.com/hc/en-us/articles/216041267-SSH-overview).
2. Navigate to the directory location you wish to create the file in or edit an existing file.
3. Type in ```vim``` followed by the name of the file. For example, if you wish to create (or edit) a new file named index.html, run the following:  

```[server]$ vim index.html```

4. Press the letter ```i``` on your keyboard to enter INSERT mode in ```vim```.
It now shows ```-- *INSERT* --``` on the bottom left:  

5. Start typing into the file.
6. When finished editing the file, press the ```ESC``` key. This takes you out of INSERT mode and ```-- INSERT --``` disappears from the bottom left of your terminal.
7. To save the file, type in a colon (:) followed by ```wq```. For example:

```:wq```


The characters ```:wq``` appear on the bottom left.  
8. Press the Enter key on your keyboard to proceed.

<a id="change"></a>  

**2-2. Changing the name of a file**

To change the name of a file, use the mv command. For example, this changes a file named file1.txt to file2.txt.

```[server]$ mv file1.txt file2.txt```

<a id="sudo"></a> 

**2-3. Using the chmod command with sudo**  

The ```sudo``` command is used to execute a command as the superuser (or root).

Executing the ```chmod``` command with ```sudo``` allows you to modify the permissions of files or directories that you do not have access to as the current user.

For example, you can use the ```sudo chmod +x``` command on a system file to give permission to all users to execute it.

```$ sudo chmod +x /sbin/reboot```

<a id="network"></a>  

### **3. Network Communication**  

**Transferring files between remote server and local system**  

- 3-1. [From Local host to the Remote host](#localremote)
- 3-2.[From Remote host to Local host](#remotelocal)
- 3-3.[Reference](#3reference)


<a id="localremote"></a>  
#### 3-1. From Local host to the Remote host

```$ scp <file_path> <user>@<remote_host>:<remote_dir>```

> ❗️ Here scp -i "key.pem" is because my remote server is on EC2. So, instead of simple SSH key based auth, EC2 uses PEM file for login. To know more about all this — [Visit this link](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html). If you already have SSH key set-up, you can skip both these terms.


<a id="remotelocal"></a>  
#### 3-2. From Remote host to Local host  

```$ scp <user>@<remote_host>:<remote_file_path> <local_dir>```

<a id="3reference"></a>   
#### 3-3. Reference   

- [Transferring files between remote server and local system](https://medium.com/dev-blogs/transferring-files-between-remote-server-and-local-system-133d78d58137)  
- [Linux sudo commands for beginners](https://www.pluralsight.com/resources/blog/cloud/linux-commands-for-beginners-sudo)

```
$  <user>@<remote_host>:<remote_file_path> <local_dir>
```




### **4. Standard Input Standard Output**  