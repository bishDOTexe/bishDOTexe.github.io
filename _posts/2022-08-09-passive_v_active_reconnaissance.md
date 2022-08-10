---
layout: post
title:  "Passive v. Active Reconnaissance"
date:   2022-08-09 21:30:00 -0400
categories: reconnaissance, OSINT
permalink: /posts/passive_v_active_reconnaissance
---

<h2>What is Reconnaissance?</h2>


Webster's defines [Reconnaissance] as 'a preliminary survey to gain information.' 
Being extremely beneficial to learn your target before you can effectively exploit and gain system level access, 
this definition perfectly fits the first step of the [Ethical-Hacker's-Methodology]. 
The key to good reconnaissance is knowing the fine boundary between active recon and passive recon. 
Within this blog post, I will describe both and teach you how to determine the difference.


<h2>-- Passive Reconnaissance --</h2>


The act of performing reconnaissance passively is tricky. 
You must gather information without directly interacting with your target. 
How is this even possible you may ask? Quite easy in fact, thanks to the power and resources of Open Source Intelligence (OSINT). 
'Open Source' meaning openly available to anyone who is willing to search for it. 
In fact, the most powerful OSINT tool is one you probably already use on a daily basis - search engines like Google and DuckDuckGo. 


When using a search engine to perform passive recon and accrue OSINT, Google is your best friend and greatest ally. 
Thanks to Google's handy [advanced-searching] features and built-in search line commands, you can truly master the art of 'Google-Fu' as some call it. 
Other passive recon tools can provide more direct information rather than just a powerful search filter. 
Some of my favorite tools include the following:


'WHOIS' - a query tool that is used primarily used for searching online domain registrar databases for domain names, 
IP address block assignments, webmaster contact information, and much more if publicly available! 
There are multiple websites that can perform this, however, more conveniently Linux CLI is capable of performing the same function. 
Debian Linux distro install and use instructions:


```
sudo apt install whois
whois --help
```


'Shodan' - A revolutionized search engine all on its own, Shodan markets itself as 'a complete picture of the internet.' 
[Shodan] allows users to search for various public facing internet devices with a variety of filters such as servers, webcams, metadata, etc. 


'Dehashed' - Another tool available via web browser. 
Dehashed is a one-stop-shop for breached/leaked usernames/emails/passwords/etc. that have all been publicly disclosed. 
Seeing the convenience of this service, there is unfortunately a strict paywall. 
Although this service is worth every penny when performing passive reconnaissance, there are alternative free options such as 'HaveIBeenPwnd' and 'WeLeakInfo.'


'WiGLE' - Wireless passive recon.. in a browser? Yes. 
[WiGLE] is extremely powerful and useful. In fact, you can geo-locate any SSID that has been broadcast, 
search SSID specifically, filter on density, etc. Properly known by the tagline 'All the networks. Found by everyone.' 
WiGLE is a powerful passive recon tool if the geo-location of your target has already been obtained and is known. 


<h2>-- Active Reconnaissance --</h2>


Compared to passive, active reconnaissance can be a bit more fun. 
With the intent to dig deeper on information found within passive recon, active reconnaissance is used to gather information such as the OS type/version, 
open ports within a network attached host, services actively running on network attached hosts, finding vulnerabilities within applications, and much more! 
Due to the nature of the act, the downside of active reconnaissance is the potential to trigger an IPS/IDS, alerting the victim organization of your intent. 
Because of this, active reconnaissance is malicious if not within the confines of a SOW or legal contract since a direct connection is performed to a victim's network property. 


<b> - - DO NOT perform Active Reconnaissance on a target without written permission and consent. 
  The author of this article will not be held responsible for the malicious use of tools/methods referred to in this article. - - </b>


Active recon can be performed in a multitude of ways. 
One of the most well known and utilized tools is Network Mapper, otherwise known as 'nmap.' 
[Nmap] is a command line tool utilized for scanning and enumerating on network IP addresses and IP address ranges. 
With a multitude of features, nmap can scan open ports on a single host, or all hosts within a specified subnet at different speeds/variations/etc. 
An entire blog post could be written on nmap alone. However, here's a link to the nmap-documentation to check out the details!


One other well known active reconnaissance tool is [Nessus]. 
This popular vulnerability assessment tool can be installed and utilized on a wide range of platforms, 
and be uniquely configured to identify critical vulnerabilities. 
Due to nature of the tool, the use of it is quite intrusive and can trigger alerts on a victim network/organization if in place. 
Based on the gathered data, Nessus will generate reports on the vulnerabilities it detects within a network and provide a list with severity ranging from Critical to Informational. 
These reports can be vital when drafting a final write-up for a client presentation on findings throughout the penetration test. 
Nessus does however require a license for professional level features, yet is a must-have for any professional Penetration Tester's arsenal. 


<h2>-- Conclusion and Summary --</h2>


Effective Reconnaissance uses many, if not all, OSINT tools to gather and obtain as much information as possible. 
Since each tool is unique, one tool or resource may pull different information than another. 
There's no such thing as too much information during the reconnaissance phase. 
For further tools that weren't mentioned in this post, check out the [GitHub-OSINT] topic. 
There are tons of great community built tools to install and utilize!
Feel free to reference an utilize the mini mind-map I've put together below for additional reference to tools and recon methodology.


![Image](https://github.com/bishDOTexe/my-images/blob/792e147ac6fefa654a998b6ab00ce36fbe28368f/Recon_mind-map.jpg?raw=true)
<img title="recon-mind-map" src="https://github.com/bishDOTexe/my-images/blob/792e147ac6fefa654a998b6ab00ce36fbe28368f/Recon_mind-map.jpg">


[Reconnaissance]: https://www.merriam-webster.com/dictionary/reconnaissance
[Ethical-Hacker's-Methodology]: https://hackmethod.com/hacker-methodology/?v=7516fd43adaa
[advanced-searching]: https://google.com/advanced_search
[Shodan]: https://shodan.io/
[WiGLE]: https://wigle.net/
[Nmap]: https://nmap.org/book/man.html#man-description
[Nessus]: [https://](https://www.tenable.com/products/nessus
[GitHub-OSINT]: https://github.com/topics/osint
