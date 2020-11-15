---
layout: post
title:  "Jekyll on WSL over Windows 10: Unable to locate package ruby2.5"
date:   2020-11-05 01:56:07 +0530
categories: jekyll update
---
*I am not going to bore you with a 2 paragraph story for a 2 line receipe - You would know what I mean if you are an impatient cook yourself who explores the web to try out new things or do your thing with a new try.*

I have Ubuntu 20.04 installed over WSL (Windows Subsystem for Linux) on Windows 10. Recently, when I was trying to install and configure Jekyll, I ran into some issues. I was trying to install ruby packages based on the instructions here: [Installation via Bash on Windows 10](https://jekyllrb.com/docs/installation/windows/#installation-via-bash-on-windows-10)

	$ sudo apt-get install ruby2.5 ruby2.5-dev build-essential dh-autoreconf
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    E: Unable to locate package ruby2.5
    E: Couldn't find any package by glob 'ruby2.5'
    E: Couldn't find any package by regex 'ruby2.5'
    E: Unable to locate package ruby2.5-dev
    E: Couldn't find any package by glob 'ruby2.5-dev'
    E: Couldn't find any package by regex 'ruby2.5-dev'


After a bit of online research (which means trying various combination of related keywords in a search engine), I came across this: [Ubuntu Package Search](https://packages.ubuntu.com/)

After selecting the distribution --> search for the available 2.* ruby version. 

![image](/blog/assets/images/Ruby_Search_in_Ubuntu.jpg)

***  
<br>
For 20.04 (focal), the available package is 2.7. [Click here to search in focal for package ruby2.*](https://packages.ubuntu.com/search?keywords=ruby2.&searchon=names&suite=focal&section=all)

Thus that version will have to be installed. Replace 2.5 with 2.7 in the command as available on the Jekyll site and you should be good to go

    sudo apt-get install ruby2.5 ruby2.5-dev build-essential dh-autoreconf


If you are new to Windows Subsystem for Linux, look [here](https://docs.microsoft.com/en-us/windows/wsl/install-win10). This contains a good quick start guide. This will also be beneficial for folks who dig Linux but use Windows as the primary OS. Instead of getting a new machine or VM, you can start using Linux right from the terminal of Windows. **Its awesome.. try it!**