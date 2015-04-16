---
layout: post
title:  " How to Set Up Your PATH Enviroment On Mac OSX"
description: set up development enviroment 
category: blog

---
## .bash_profile
Have you ever wondered that when you type in commonad, like $ python in a terminal. How does your system know the meaning of python and the path of commoand $ python. All the magics lie
in a shell script called .bash_profile.(for the
difference between .bash_profile and .bashrc, 
go to this page for [details][detailsurl])
Basically, this script get excuted everytime when you start a log in shell and tell the system
where to find the path. 

## Set Up Environment 
I first encountered with this question when I tried
to use maven for my project.It had a hard time finding path for java sdk. I checked out all kinds of resources online trying to figure out the correct syntax to set path in bash_profile and 
it was so painful. At the end, I figured out two
ways fo set up path,

the first one is:
<code>
PATH="/Library/Frameworks/Python.framework/Versions/3.4/bin:${PATH}"
PATH="/Users/taoyiran/apache-maven-3.2.2/bin:${PATH}"
PATH="/usr/local/:mysql/bin:${PATH}"</code>

the other one is:
<code>
export JAVA_HOME=/usr/libexec/java_home
export TOMCAT_HOME=/usr/local/apache-tomcat-7.0.50
export ECLIPSE_HOME=/usr/local/eclipse
export M2_HOME=/usr/local/apache-maven-3.1.1
export MYSQL_HOME=/usr/local/mysql-5.6.14-osx10.7-x86_64
export PATH=$JAVA_HOME/bin:$ECLIPSE_HOME:$M2_HOME/bin:$MYSQL_HOME/bin:$TOMCAT_HOME/bin:$PATH
</code>

Hope this will help you !

## ok
 
[detailsurl]:http://www.joshstaiger.org/archives/2005/07/bash_profile_vs.html
[github]: https://github.com/tyr034


