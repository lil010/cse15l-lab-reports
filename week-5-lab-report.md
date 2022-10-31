# Week 3 Lab Report

## Command I chose: ```find```

## Command Line 1: ```-amin n```

This command line is used for finding file that was last accessed n minutes ago.

### Example 1:

```
[cs15lfa22at@ieng6-202]:technical:224$ cat plos/pmed.0020226.txt

Richard Smith's key suggestion [1] is that medical journals “should stop publishing trials” and concentrate on “critically evaluating them.” This bold and radical suggestion deserves wide debate. It's obvious that many medical journals are losing relevance as vehicles for scientific information, but it's unclear what will save them. Even as journals strive to better enforce their conflicts-of-interest disclosure rules, drug companies will strive to find or create other publication outlets that can communicate to physicians precisely what advertisers wish to communicate. In sum, an unanticipated effect of purging clinical trial reports from medical journals might be an even larger proliferation of frank advertising outlets and messages that might more effectively catch doctors' attentions.



[cs15lfa22at@ieng6-202]:technical:225$ find -amin 1
./plos/pmed.0020226.txt
```

This example is to show that the ```-amin``` command can be used to search the file that is accessed n minutes ago with the parameter being integer ```n```. In this example, I chose to concatenate prints the content in the file *pmed.0020226.txt* from the directory *plos* by using command line on 224$ above. Then, as the command successfully executed, it prints out the content of the file. Next, I used command on 225$ to find a file that I was accessed 1 minute ago, and the terminal returns the file *pmed.0020226.txt* as expected. 

It is also noteworthy that the parameter ```n``` is a round-up minutes. For example, if I try to use ```-amin 1``` in a directory, it would show the file that I accessed 1 second to 60 seconds ago. 

### Example 2:

```
[cs15lfa22at@ieng6-202]:technical:263$ find -amin 5
[cs15lfa22at@ieng6-202]:technical:264$
```

This example shows that the command line is used to show that the parameter ```n``` is an accurate minute of time that a file is accessed. Even though I used ```cat``` command to a file 2 minutes ago, it would not being returned, as the output of the command line is based on a precise minute but not a range of time. 

### Example 3:

```
[cs15lfa22at@ieng6-202]:technical:269$ cat plos/pmed.0020226.txt plos/pmed.0020191.txt

Richard Smith's key suggestion [1] is that medical journals “should stop publishing trials” and concentrate on “critically evaluating them.” This bold and radical suggestion deserves wide debate. It's obvious that many medical journals are losing relevance as vehicles for scientific information, but it's unclear what will save them. Even as journals strive to better enforce their conflicts-of-interest disclosure rules, drug companies will strive to find or create other publication outlets that can communicate to physicians precisely what advertisers wish to communicate. In sum, an unanticipated effect of purging clinical trial reports from medical journals might be an even larger proliferation of frank advertising outlets and messages that might more effectively catch doctors' attentions.


The excellent article by Jordan Paradise, Lori B. Andrews, and colleagues, “Ethics. Constructing Ethical Guidelines for Biohistory” [1], neither advocates nor argues against biohistorical research; instead, it points out that such investigations are currently taking place without guidelines—ethical, scientific, moral, or religious. The question remains: if such guidelines were to be established, what individuals, institutions, governments, medical examiners, family members, or intrepid biographers are to be given permission? Who is to decide what is “historically significant”? Not to mention the meta-question: who is to decide who is to decide? I apologize to the authors if my brief comments [2] implied that they took a position on this issue.



[cs15lfa22at@ieng6-202]:technical:270$ find -amin 1
./plos/pmed.0020191.txt
```

We can observed from this example that ```-amin n``` command line only return a file when inputing the minute when a file is accessed for the first time, and otherwise it would not be in output. We had accessed *pmed.0020226.txt* by ```cat``` in example 1 several minutes ago, and we try to access it with another file *pmed.0020191.txt* this time by using the same command ```cat``` in line $269. However, *pmed.0020226.txt* is not shown in the result of ```-amin 1``` in the return output of line $270, because it had been accessed several minutes ago for the first time. Hence, *pmed.0020191.txt* is the only output. 

The ```-amin n``` command is useful when trying to achieve a file when you remember that has been accessed in several minutes ago by you, and its accuracy in minutes help users to sort the accessed files by accessing time. However, it has a limit that it only reaches the time a file is accessed for the first time. Hence, it would be useful as an instant helper command. 

## Command Line 2: ```-mmin n```

This command line is used for finding file that was last modified n minutes ago.

### Example 1:

```
PS C:\Users\lilit\OneDrive\Documents\GitHub\docsearch> scp technical/911report/chapter-1.txt cs15lfa22at@ieng6.ucsd.edu:~/docsearch/technical/911report
chapter-1.txt                                                                                                                      100%  117KB 899.7KB/s   00:00     
PS C:\Users\lilit\OneDrive\Documents\GitHub\docsearch> ssh cs15lfa22at@ieng6.ucsd.edu
Last login: Sun Oct 30 15:12:14 2022 from 108-216-108-197.lightspeed.sndgca.sbcglobal.net
quota: Cannot resolve mountpoint path /home/linux/ieng6/.snapshot/hourly.2022-10-10_0801: Stale file handle
quota: Cannot resolve mountpoint path /home/linux/ieng6/.snapshot/hourly.2022-10-10_1201: Stale file handle
Hello cs15lfa22at, you are currently logged into ieng6-202.ucsd.edu

You are using 0% CPU on this system

Cluster Status 
Hostname     Time    #Users  Load  Averages  
ieng6-201   15:25:01   10  0.06,  0.10,  0.07
ieng6-202   15:25:01   6   0.07,  0.09,  0.12
ieng6-203   15:25:01   13  4.09,  4.14,  4.14

 
Sun Oct 30, 2022  3:26pm - Prepping cs15lfa22
[cs15lfa22at@ieng6-202]:~:231$ cd docsearch
[cs15lfa22at@ieng6-202]:docsearch:232$ cd technical
[cs15lfa22at@ieng6-202]:technical:234$ find -mmin 2
./911report/chapter-1.txt
```

In this example, I modified the file *chapter-1.txt* in ieng6 by save copying the local file *chapter-1.txt* by using the command ```scp technical/911report/chapter-1.txt cs15lfa22at@ieng6.ucsd.edu:~/docsearch/technical/911report```. After that, I save shell logged in ieng6 by using ```ssh cs15lfa22at@ieng6.ucsd.edu``` and changed the directory by using the code in line 231$ and 232$. In technical directory, I used command line ```-mmin 2``` in order to find the file I edited 1 minutes to 2 minutes ago, so it return the path of *chapter-1.txt*.

It is also noteworthy that like ```-amin n```, the parameter ```n``` is also a round-up minutes. For example, if I try to use ```-mmin 1``` in a directory, it would show the file that I accessed 1 second to 60 seconds ago. 

### Example 2:

```
PS C:\Users\lilit\OneDrive\Documents\GitHub\docsearch> scp technical/911report/chapter-1.txt technical/911report/preface.txt cs15lfa22at@ieng6.ucsd.edu:~/docsearch/technical/911report
chapter-1.txt                                                                                                                      100%  117KB 910.3KB/s   00:00     
preface.txt                                                                                                                        100% 9440    28.6KB/s   00:00

//I skipped the login input and output here for saving space of the lab report.

[cs15lfa22at@ieng6-202]:~:273$ cd docsearch/technical
[cs15lfa22at@ieng6-202]:technical:274$ find -mmin 1
./911report/chapter-1.txt
./911report/preface.txt
```

I tried to use the command to 2 files and it worked. I modified the file *chapter-1.txt* and *preface* in ieng6 by save copying the local file *chapter-1.txt* and *preface* by using the command ```scp technical/911report/chapter-1.txt technical/911report/preface.txt cs15lfa22at@ieng6.ucsd.edu:~/docsearch/technical/911report```, and went through the login and changing directory step that is the same with that in example 1. In technical directory, I used command line ```-mmin 1``` in order to find the file I edited 0 minutes to 1 minutes ago, so it return the path of *chapter-1.txt* and *preface.txt*. Hence, different than the ```-amin n``` command, ```-mmin n``` command takes in the minute that a file is edited for the last time.

### Example 3:

```
[cs15lfa22at@ieng6-202]:technical:275$ find -mmin 10
[cs15lfa22at@ieng6-202]:technical:276$
```

This example shows that the command line is used to show that the parameter ```n``` is an accurate minute of time that a file is modified. Even though I used ```scp``` command to a file 5 minutes ago, it would not being returned, as the output of the command line is based on a precise minute but not a range of time. 

This command line is useful when trying to find a file that is modified n minutes ago. Sometimes when you are struggling with a bunch of files that you edited a few minutes ago and could not remember the name of a file you are sure that were modified, you can use the command line to approach the file. You can also do it for multiple files. 

## Command Line 3: ```-size n[cwbkMG]```

This command line is used to find the file that has a certain size of n units in the directory. The letter in parameter represented: 

* `b'    for 512-byte blocks (this is the default if no suffix is used)
* `c'    for bytes
* `w'    for two-byte words
* `k'    for Kilobytes (units of 1024 bytes)
* `M'    for Megabytes (units of 1048576 bytes)
* `G'    for Gigabytes (units of 1073741824 bytes)

## Example 1:

```
[cs15lfa22at@ieng6-202]:technical:276$ find -size 48k
./biomed/1471-2121-3-4.txt
./biomed/1471-213X-3-4.txt
./biomed/1471-2148-1-8.txt
./biomed/1471-2350-3-1.txt
./biomed/1472-6807-2-3.txt
./biomed/1472-6882-3-1.txt
./biomed/1477-7827-1-46.txt
./biomed/gb-2001-2-12-research0055.txt
./biomed/gb-2002-3-12-research0085.txt
./biomed/gb-2002-3-7-research0035.txt
./biomed/gb-2002-4-1-r2.txt
```

I used command ```find -size 48k``` to search the files that has a size of 48 kilobytes under technical directory, and the output returned the path of files that have the exact same size that I was asking for in the parameter. 


## Example 2:

```
[cs15lfa22at@ieng6-202]:technical:277$ find -size +41k -size -43k
./biomed/1471-2121-2-11.txt
./biomed/1471-213X-1-2.txt
./biomed/1471-2202-3-16.txt
./biomed/1471-2202-4-11.txt
./biomed/1471-2288-2-10.txt
./biomed/1472-6793-1-8.txt
./biomed/1472-6890-1-4.txt
./biomed/1472-6947-2-7.txt
./biomed/1476-4598-2-24.txt
./biomed/gb-2001-2-6-research0018.txt
./biomed/gb-2002-3-12-research0082.txt
./biomed/gb-2003-4-2-r11.txt
./government/Post_Rate_Comm/Cohenetal_CreamSkimming.txt
./plos/pmed.0020073.txt
```

In this example, I used a trick of ```-size``` command that it can take in a lower bound of size as ```+n``` and an upper bound of size as ```-n```. To be specific, I used command ```find -size +41k -size -43k``` to search the files that has a size in the range of 41 to 43 kilobytes under technical directory, and the output returned the path of files that have the size in the range that I was asking for in the parameter.

## Example 3:

```
[cs15lfa22at@ieng6-202]:technical:278$ find -size +1M -size -2M
[cs15lfa22at@ieng6-202]:technical:279$
```

In this example, I used command ```find -size +1M -size -2M``` to search the files that has a size in the range of 1 to 2 megabytes under technical directory. However, it doesn't return, which explains that there is no file that has a size between 1 to 2 megabytes.

This command line is useful when you want to search for name of the files that have a certain size of unit in the directory. It is also useful to determine the range of the size of files, and this data can be used for calculations and other functions. 