---
layout: post
title:  "Directory Enumeration using 'gobuster'"
date:   2022-07-13 08:40:00 -0400
categories: enumeration, gobuster
permalink: /posts/directory_enumeration_using_gobuster
---


<h1>Enumeration Explained</h1>

Enumeration is a vital part of the Ethical Hacker Methodology step known as reconnaissance. 
To put it plain and simple, you want as much information as possible in order to effectively attack your target. Agree? Agree! 

First, lets define what Enumeration is. [Enumeration] is the act or process of making or stating a list of things one after another.
This could means making a list of potential vulnerabilites, potential weaknesses, etc. 
One specific instance of enumeration is the enumeration of a website and it's sub-directories. 
When you think of a website - all of the site pages, setup files, images, have to be stored somewhere on the hosting server - right? Correct.

Depending on the developer/architect of the website, and how security driven their mindset is, some key information could still be public. 
Even if a developer excludes links from public facing pages and proper restrictions are not in place, the information may still be indirectly exposed.
This is where directory enumeration comes into play. 

As a practical example, lets say that during an nmap scan of 10.10.2.0/24, you identify open http/https ports 80/443 on 10.10.2.5. 
Because of this, you navigate to 10.10.2.5 within a web browser. 
You could begin randomly appending '/admin' or '/login' to the end of the URL to see if anything exists and successfully loads a page. 
Or, you could install and utilize a directory enumeration tool such as 'gobuster'.

<h1>gobuster Installation</h1>

One specific tool that can help us as Ethical Hackers perform website enumeration is a tool I have grown quite fond of - gobuster. G
obuster is written in the language 'go' which was developed by Engineers at Google being statically typed and similar to the C programming language. 
Due to the availability within some distros of linux OS and select package installers, the latest version may not always be installed directly. 
A separate install of 'go' can be performed and the updated GitHub repository pulled from [HERE]. 
See basic linux package install instructions below. 

```
sudo apt install gobuster
```

Once installed, check the version of gobuster that was installed from default linux OS repositories. 
As of the time of publishing this article, gobuster is currently on stable public release 3.1.0.

```
gobuster version
```

<b> - Be Advised - </b>

<b>This tool is quite noisy and aggressive. Only use this tool against domains you have written authority to scan.</b>

<h1>gobuster Command Modules Overview</h1>

Gobuster has several available commands. 
Although 'dir' is most commonly used when first learning the tool, 'dns' and 'fuzz' are also commonly utilized when enumerating with gobuster. 
Specifically in 3.1.0 the following command modules are available:

```
┌──(kali㉿kali)-[~]
└─$ gobuster --help         
Usage:
  gobuster [command]

Available Commands:
  dir         Uses directory/file enumeration mode
  dns         Uses DNS subdomain enumeration mode
  fuzz        Uses fuzzing mode
  help        Help about any command
  s3          Uses aws bucket enumeration mode
  version     shows the current version
  vhost       Uses VHOST enumeration mode
```

<h1>gobuster 'dir' Command Module</h1>

Before we begin, it's important for us to investigate and verify the required and optional flags when using the dir module in gobuster. 
These can be found from again utilizing the '--help' flag after specifying dir. Due to the lengthy output, I will only include the syntax to view the flags below. For an in-depth look at all 'dir' flags, use this [direct-link] to the GitHub repo page.

```
┌──(kali㉿kali)-[~]
└─$ gobuster dir --help                                                                             
Uses directory/file enumeration mode

Usage:
  gobuster dir [flags]
```

Required flags for utilizing the dir module is -u and -w. '-u' references the URL to run the directory enumeration and '-w' utilizes a specified word list. 
From our practical example at the beginning of this post, the required syntax would look something like this: 

```
┌──(kali㉿kali)-[~]
└─$ gobuster dir -u http://10.10.2.5 -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt 
```

<i> - In addition to the above default dirbuster wordlist directory, you can also reference other great publicly available wordlists for use! 
One example is [SecLists], a popular public GitHub repo. Feel free to download and experiement with any wordlist you're able to find (since the provided is just one example of many) and see which you find most useful! - s</i>

Once the initial directory completes, any sub-directories you find that look particularly interesting can be expanded upon by performing another gobuster dir scan. For example, if '/admin' was found from the initial scan, you can run another specifying '10.10.2.5/admin' to perform a more granular directory enumberation scan seen below.

```
gobuster dir -u http://10.10.2.5/admin -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt 
```

Another helpful flag for directory enumeration is the '-o' flag to output the results to a file for reference later on. 
Keep in mind, the output flag will require a directory specification, or simply a file name if you'd like the output to save to the current working directory.

Maintaing a standard of outputting results to a file for future reference is extremely important as well for maintaining good notes. 
During enumeration, and again referencing our initial definition from websters, your entire goal is to create a list and map out gathered information to understand and learn as much as possible about your target. Not only to make your pentest easier, but also to provide your client with as much detailed information you learn through the process. There is no such thing as too much information during the reconnaissance phase! 

<h1>Conclusion</h1>

As you can see, gobuster is an extremely powerful yet lightweight tool for enumerating directories within a web server! As I continue to progress in my pentesting career, I may come back to update this article with further use cases and information. If you feel I have incorrectly cited information, please feel free to reach me at my email in the blog page footer. Thank you for reading!

[Enumeration]: https://www.merriam-webster.com/dictionary/enumeration
[HERE]: https://github.com/OJ/gobuster/
[SecLists]: https://github.com/danielmiessler/SecLists
[direct-link]: https://github.com/OJ/gobuster#dir-mode-options
