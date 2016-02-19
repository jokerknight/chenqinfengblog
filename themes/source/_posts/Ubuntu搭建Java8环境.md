title: " Ubuntu build Java8 environment"
date: 2016-02-18 17:54:00 
categories: [服务器 ]
tags: [Java8,Ubuntu,apt-get install java ubuntu]
---


# Ubuntu build Java8 environment

## Check if exsit

```java
java -version
```
if exsit will prompt that your current installed java version.
## Install
First you need to add webupd8team Java PPA repository in your system and install Oracle Java 8 using following set of commands.
```java
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt-get update
$ sudo apt-get install oracle-java8-installer
```
## Verify and check again
```java
root@ubuntu:/home/app# java -version
java version "1.8.0_72"
Java(TM) SE Runtime Environment (build 1.8.0_72-b15)
Java HotSpot(TM) 64-Bit Server VM (build 25.72-b15, mixed mode)

```
## Configuring Java Environment

In Webupd8 ppa repository also providing a package to set environment variables, Install this package using following command.
```java
$ sudo apt-get install oracle-java8-set-default
```
## Finally
Congratulations! you have success installed java8 in your ubuntu!