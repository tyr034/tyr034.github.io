---
layout: post
title: Python Email Crawler
description: 
category: blog
---

 

## Python Email Crawler:
Fives lines to print all email address from any web page


	import urllib.request
	import re 
	response = urllib.request.urlopen("http://www.bu.edu/cs/people/directory/")
	myfile = response.read().decode('utf-8')
	emails = set(re.findall(r'[\w\.-]+@[\w\.-]+',myfile))
	for email in emails:
    	print(email)


