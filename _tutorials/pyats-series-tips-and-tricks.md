---
published: false
date: '2023-04-26 16:09 +0200'
title: pyats-series-tips-and-tricks
position: hidden
author: Antoine Orsoni
tags:
  - iosxr
  - cisco
---
![pyats_hello2.jpg]({{site.baseurl}}/images/pyats_hello2.jpg){: .align-center}

# Introduction

Ever dreamed of a test framework that could be used across multiple platforms, OS and vendors, which could do regression, sanity and feature testing; already used by thousands of engineers and developers worldwide? Guess what, **it exists, it’s free, and you can start using it right now!**

pyATS (**Py**thon **A**utomated **T**est **S**ystems, to be pronounced "py A. T. S.") was first created as an internal project, to ease the validation of two OS versions. It has been made public in 2017 through **Cisco Devnet**.

This blog post will be the second one of a series on pyATS. Today, we will explore pyATS libraries (also known as Genie), and we will collect our first **parsed output**. More use cases are going to be covered in the next posts. 

# Other pyATS episodes

You've missed the first episode? You would like to read more? Below the list of published episodes:

| Episode 	| URL                                                                                              	| What's covered                                        	|
|---------	|--------------------------------------------------------------------------------------------------	|-------------------------------------------------------	|
| **1 - Install and use pyATS**       	| [Link](https://xrdocs.io/programmability/tutorials/pyats-series-install-and-use-pyats/){: .btn}  	|  What's pyATS, Install pyATS, Collect a raw CLI output 	|
| **2 - Parsing like  a pro**       	| [Link](https://xrdocs.io/programmability/tutorials/pyats-series-parsing-like-a-pro/){: .btn} 	|  Explore pyATS libraries, Collect and parse a CLI output        	|
| **3 - Be a model**       	| [Link](https://xrdocs.io/programmability/tutorials/pyats-series-be-a-model/){: .btn} 	|  What a pyATS model and when to use it        	|
| **4 - Collecting many show commands**       	| [Link](https://xrdocs.io/programmability/tutorials/pyats-series-collecting-many-show-commands/){: .btn} 	|  How to collect many show commands on many devices?

# pyATS tool belt

## pyATS installation and maintenance

### Installing pyATS

After checking the [Requirements](https://pubhub.devnetcloud.com/media/pyats-getting-started/docs/prereqs/prerequisites.html#requirements), you can install pyATS and pyATS librairies by running the below command.

```
pip install "pyats[full]"
```

### Veryfying the installation

You can verify pyATS has been successfuly installed by running the below command. It should return the current pyATS version, with a similar output. This command also shows if there are any available package updates.

```
pyats version check

You are currently running pyATS version: 23.3
Python: 3.10.4 [64bit]

  Package                      Version
  ---------------------------- -------
  genie                        23.3   
  genie.libs.clean             23.3   
  
  ## output chunked for brevity ## 
  
  yang.connector               23.3   
```

### Updating pyATS

You can check if there is a newer pyATS version and update it with the below command. It should return a similar output.

```
pyats version update

Checking your current environment...


The following packages will be removed:

  Package                      Version
  ---------------------------- -------
  genie                        23.3   
  genie.libs.clean             23.3   
    
  ## output chunked for brevity ## 
 
  unicon.plugins               23.3   
  yang.connector               23.3   


Fetching package list... (it may take some time)

... and updated with:

  Package                      Version      
  ---------------------------- -------------
  genie                        latest (23.4)
  genie.libs.clean             latest (23.4)

## output chunked for brevity ## 

  unicon.plugins               latest (23.4)
  yang.connector               latest (23.4)


Are you sure to continue [y/N]? 
```