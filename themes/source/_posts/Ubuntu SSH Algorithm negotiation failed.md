title: "Ubuntu SSH Algorithm negotiation failed"
date: 2016-02-19 11:38:00 
categories: [服务器]
tags: [ssh,Ubuntu,Algorithm negotiation failed]
---


# Ubuntu SSH Algorithm negotiation failed

## Situation

```java
Server responded"Algorithm negotiation failed"
Key exchange with the remote host failed. This can happen for
example computer does not support the selected  
algorthms. ```

When ssh to a ubuntu system,putty can connect but 'SSH Secure Shell Client' is failed,according to the pop-up error message we can know that 
the algorithm negotiation failed, after searching high-and-low for this fix, I finally found it’s fix…

## Reason
Because i had past updated server, it's that means i had updated the sshd algorithm negotiation on server meanwhile, but the sshd algorithm negotiation in  client is the old, so server cannot compatible the algorithm negotiation from client.

## The Way to resolve 
1. Use a different system or the console to drop to a shell. Such as Putty 
2. Chmod 777 & Edit the "/etc/ssh/sshd_config" file 
3. Add all of the algorithm negotiation to sshd_config  
4. Restart sshd sevice
Add following code to sshd_config

```java
Ciphers aes128-cbc,aes192-cbc,aes256-cbc,aes128-ctr,aes192-ctr,aes256-ctr,3des-cbc,arcfour128,arcfour256,arcfour,blowfish-cbc,cast128-cbc

MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-sha1-96,hmac-md5-96

KexAlgorithms diffie-hellman-group1-sha1,diffie-hellman-group14-sha1,diffie-hellman-group-exchange-sha1,diffie-hellman-group-exchange-sha256,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group1-sha1,curve25519-sha256@libssh.org```



```java
root@ubuntu:/home/app# chmod 777 /etc/ssh/sshd_config
root@ubuntu:/home/app# vi /etc/ssh/sshd_config
root@ubuntu:/home/app# service sshd restart

```

## Finally
Congratulations! you have success resolved Algorithm negotiation failed