---
layout: post
title: Kringlecon 2 - 2019 SANS Hack Holiday Challenge Write-up
date:   2020-01-13
description: Every year around the holidays SAN releases their CTF Holiday Hack challenge. These Holiday Hack challenges consists of a story and a mystery that revolve around the holidays and Santa. This write-up will provide a walkthrough of the Holiday Hack Challenge. It includes a walkthrough of each objectives and terminal challenge. It will also provide inspiring quotes, hints and strategies on solving future challenges.

tags:
- CTF
- REM


share: true
toc: false
---

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image01.PNG" alt="">
    <br>
    Kringlecon 2 - Holiday Hack Challenge 2019
</div><br>

[Kringlecon 2 - Holiday Hack Challenge 2019](https://holidayhackchallenge.com/2018/story.html)



## Table of Content
1. [Introduction](#Introduction)
    - [Protips](#Protips)
    - [Holiday Hack Challenge Logo](#Holiday-Hack-Challenge-Logo)
1. [Objective 0 - Talk to Santa in the Quad](#Objective-0---Talk-to-Santa-in-the-Quad)
1. [Objective 1 - Find the Turtle Doves](#Objective-1---Find-the-Turtle-Doves)
1. [Objective 2 - Unredact Threatening Document](#Objective-2---Unredact-Threatening-Document)
1. [Objective 3 - Windows Log Analysis: Evaluate Attack Outcome](#Objective-3---Windows-Log-Analysis:-Evaluate-Attack-Outcome)
    - [Escape Ed - Terminal Challenge](#Escape-Ed---Terminal-Challenge)
    - [Objective 3 - Walkthrough](#Objective-3---Walkthrough)
1. [Objective 4 - Windows Log Analysis: Determine Attacker Technique](#Objective-4---Windows-Log-Analysis:-Determine-Attacker-Technique)
    - [Linux Path - Terminal Challenge](#Linux-Path---Terminal-Challenge)
    - [Objective 4 - Walkthrough](#Objective-4---Walkthrough)
1. [Objective 5 - Network Log Analysis: Determine Compromised System](#Objective-5---Network-Log-Analysis:-Determine-Compromised-System)
    - [Xmas Cheer Laser - Terminal Challenge](#Xmas-Cheer-Laser---Terminal-Challenge)
    - [Objective 5 - Walkthrough](#Objective-5---Walkthrough)
1. [Objective 6 - Splunk](#Objective-6---Splunk)
    - [Splunk Training Questions - Terminal Challenge](#Splunk-Training-Questions---Terminal-Challenge)
    - [Objective 6 - Walkthrough](#Objective-6---Walkthrough)
1. [Objective 7 - Get Access To The Steam Tunnels](#Objective-7---Get-Access-To-The-Steam-Tunnels)
    - [Frosty Keypad Challenge](#Frosty-Keypad-Challenge)
    - [Holiday Hack Trial - Terminal Challenge](#Holiday-Hack-Trial---Terminal-Challenge)
    - [Objective 7 - Walkthrough](#Objective-7---Walkthrough)
1. [Objective 8 - Bypassing the Frido Sleigh CAPTEHA](#Objective-8---Bypassing-the-Frido-Sleigh-CAPTEHA)
    - [Nyanshell - Terminal Challenge](#Nyanshell---Terminal-Challenge)
    - [Objective 8 - Walkthrough](#Objective-8---Walkthrough)
1. [Objective 9 - Retrieve Scraps of Paper from Server](#Objective-9---Retrieve-Scraps-of-Paper-from-Server)
    - [Graylog - Terminal Challenge](#Graylog---Terminal-Challenge)
    - [Objective 9 - Walkthrough](#Objective-9---Walkthrough)
1. [Objective 10 - Recover Cleartext Document](#Objective-10---Recover-Cleartext-Document)
    - [Mongo Pilfer - Terminal Challenge](#Mongo-Pilfer---Terminal-Challenge)
	- [Objective 10 - Walkthrough](#Objective-10---Walkthrough)
1. [Objective 11 - Open the Sleigh Shop Door](#Objective-11---Open-the-Sleigh-Shop-Door)
    - [Smart Braces - Terminal Challenge](#Smart-Braces---Terminal-Challenge)
    - [Objective 11 - Walkthrough](#Objective-11---Walkthrough)
1. [Objective 12 - Filter Out Poisoned Sources of Weather Data](#Objective-12---Filter-Out-Poisoned-Sources-of-Weather-Data)
    - [Zeek JSON Analysis - Terminal Challenge](#Zeek-JSON-Analysis---Terminal-Challenge)
    - [Objective 12 - Walkthrough](#Objective-12---Walkthrough)
1. [Conclusion](#Conclusion)

<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div><br>

## Introduction
Every year around the holidays SAN releases their CTF Holiday Hack challenge. These Holiday Hack challenges consists of a story and a mystery that revolve around the holidays and Santa.

As a player, you get to interact with a 2D world and work on solving challenges. Solving these challenges help players unravel the mystery of the holidays. As a result the players are put in a though spot to help Santa and save christmas.

This year's challenge is located at Elf university. There are 12 main objectives to solve in this year's challenge. The objectives have varying  difficulty level, from 1 to 5 (easiest to hardest).

The players can receive hints for the main objectives by solving mini challenges called terminal challenges. As players solve each objective and terminal challenge, they receive badges.

As part of the holiday hack challenge, SANs releases a number of educational videos that may be helpful for solving the objectives.

This write-up will provide a walkthrough of the Holiday Hack Challenge. It includes a walkthrough of each objectives and terminal challenge. It will also provide inspiring quotes, hints and strategies on solving future challenges.

Links:

- [Holiday Hack Challenge 2019](https://holidayhackchallenge.com/2019/)
- [Free Album](https://holidayhackchallenge.com/2019/music.html)
- [KringleCon 2019 Videos](https://www.youtube.com/playlist?list=PLjLd1hNA7YVzyhhqBQaW-tF45xnS6oHAP)

<br>
### Protips
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image02.PNG" alt="">
    <br>
    Kringlecon 2 - What You Can Do
</div><br>  

---
My strategy for tackling each objective is as follow:
- Solve the Terminal Challenges
- Watch all the Videos
- Tackle the Objective
- Document and take screenshots as progressing through the game.

---
A tip from John Hammond to hold predominance over the universe:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image09.PNG" alt="">
    <br>
    Kringlecon 2 - The Infinity <strike>Stone</strike> Step
</div><br>  
The Pwn step is a function for the domain that you're trying to achieve predominance. It's a multidimensional thing.


---

There is a good series of tips by Katie Knowles in this conference. They can be watched [here](https://www.youtube.com/watch?v=c02mH7F1xvU).
Here is some keypoints of this talk:


> Know your what and how!

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image239-2.PNG"
     alt="">
    <br>
    Kringlecon 2 - How to Hack
</div><br>  


> How to Hack!

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image240.PNG"
     alt="">
    <br>
    Kringlecon 2 - How to Hack
</div><br>  

> The problem spiral, which in some ways is the pwn step of the infinity <strike> stone </strike> step:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image241.PNG"
     alt="">
    <br>
    Kringlecon 2 - How to Hack!
</div><br>  

> Read this book!

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image242.PNG"
     alt="">
    <br>
    Kringlecon 2 - Read this book before bed.
</div><br>  


---

### Holiday Hack Challenge Logo
If you're not feeling warm and fuzzy yet with your hot chocolate, don't worry you'll get there.

This year's logo looked interesting. Lets take a look at the logo.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image238.PNG"
     alt="">
    <br>
    Kringlecon 2 - ELF University Logo
</div><br>  

There is latin on the logo ```Ille Te videt dum dormit```.

Using google translator, it gives two different possible translation:

```
Ille Te videt dum dormit = We see him while he sleeps
Ille Te videt = He sees you
dum dormit = while sleeping
```

Then there is this all seeing eye on the logo.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image239.PNG"
     alt="">
    <br>
    Kringlecon 2 - Santa's All Seeing Eye?
</div><br>  

Here are some of the rejected Logos:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image28.PNG"
     alt="">
    <br>
    Kringlecon 2 - 'rejected-elfu-logos.txt'
</div><br>  

Hopefully you're feeling warm and fuzzy by now. Lets start the Holiday hack challenge!

---

<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div><br>


## Objective 0 - Talk to Santa in the Quad

|    |       |
|----|-------|
|Inspirational Quote| "A positive attitude will help you and the world." -hacks4pancake |
|Objective|Enter the campus quad and talk to Santa.|
|Difficulty Level:|0|
|Links| n/a|  
|Related Video| [Lesley Carhart, Over 90,000: Ups and Downs of my InfoSec Twitter Journey](https://www.youtube.com/watch?v=RplOa_lqXvk&list=PLjLd1hNA7YVzyhhqBQaW-tF45xnS6oHAP) |  

<br>
### Objective 0 - Walkthrough
As you enter the game you're greeted by Santa. He has the following message for you:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image04.PNG" alt="">
    <br>
    Kringlecon 2 - Santa at Entrance
</div><br>  


<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image03.PNG" alt="">
    <br>
    Kringlecon 2 - Santa's Message
</div><br>  

As you explore and enter the campus quad, you find Santa waiting there.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image05.PNG" alt="">
    <br>
    Kringlecon 2 - Santa in Campus
</div><br>  


<br>
### Objective 0 - Solution
Answer:
```
Talk to Santa in Campus.
```

He has the following message for you which starts the game:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image06.PNG" alt="">
    <br>
    Kringlecon 2 - Storyline
</div><br>  

---

<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div><br>

## Objective 1 - Find the Turtle Doves

|    |       |
|----|-------|
|Inspirational Quote| "In our hacker community, we're all family." -John Hammond |
|Objective| Find the missing turtle doves.|
|Difficulty Level:| 0|
|Links| n/a|  
|Related Video| [John Hammond, 5 Steps to Build and Lead a Team of Holly Jolly Hackers](https://www.youtube.com/watch?v=D5Nwg84cV1E&list=PLjLd1hNA7YVzyhhqBQaW-tF45xnS6oHAP)|

<br>
### Objective 1 - Walkthrough
As you walk and explore the campus you get to see the different areas you have access to.

Once you explore the student union, you will find the solution to this challenge.
<br>
#### Objective 1 - Solution
Answer:
```
Dove's are in the student union by the fireplace.
```
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image07.PNG" alt="">
    <br>
    Kringlecon 2 - Michael and Jane - Two Turtle Doves
</div><br>  


Very important message from the Doves:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image08.PNG" alt="">
    <br>
    Kringlecon 2 - Message from the Doves
</div><br>  

---
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div><br>

## Objective 2 - Unredact Threatening Document

|        |       |
|--------|-------|
|Inspirational Quote| "Pull That Thread." -Good Elf |
|Objective|Someone sent a threatening letter to Elf University. What is the first word in ALL CAPS in the subject line of the letter? Please find the letter in the Quad.|
|Difficulty Level:|1|
|Links| [LetterToElfUPersonnel.pdf](https://downloads.elfu.org/LetterToElfUPersonnel.pdf)|  
|Related Video|[Heather Mahalik, When Malware Goes Mobile, Quick Detection is Critical](https://www.youtube.com/watch?v=IEbLOvT4Fts&list=PLjLd1hNA7YVzyhhqBQaW-tF45xnS6oHAP)|


<br>
### Objective 2 - Walkthrough
As you walk around the quad and explore you find the following document in north west corner of the quad.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image10.PNG" alt="">
    <br>
    Kringlecon 2 - LetterToElfUPersonnel.pdf
</div><br>  

As you open the document and examine it, you notice that you can highlight everything in the document.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image11.PNG" alt="">
    <br>
    Kringlecon 2 - LetterToElfUPersonnel.pdf content
</div><br>  


You select everything and press 'CTRL-C' to copy everything.

You paste the content in a text editor to view the message:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image12.PNG"
     alt="">
    <br>
    Kringlecon 2 - LetterToElfUPersonnel.pdf content
</div><br>  

<br>
#### Objective 2 - Solution
Answer:
```
DEMAND
```

---
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div><br>
## Objective 3 - Windows Log Analysis: Evaluate Attack Outcome

|    |       |
|----|-------|
|Inspirational Quote| "<strike>Roads?</strike> Logs? Where we're going we don't need <strike>Roads</strike> Logs." -Mark Baggett |
|Objective|We're seeing attacks against the Elf U domain! Using the event log data, identify the user account that the attacker compromised using a password spray attack. Bushy Evergreen is hanging out in the train station and may be able to help you out.|
|Difficulty Level:|1|
|Links| [Security.evtx.zip](https://downloads.elfu.org/Security.evtx.zip)|  
|Related Video|[Mark Baggett, Logs? Where we're going we don't need logs](https://www.youtube.com/watch?v=Dx78oObfiBM&list=PLjLd1hNA7YVzyhhqBQaW-tF45xnS6oHAP)|
|Tools| [SRUM-DUMP](https://github.com/MarkBaggett/srum-dump), [ESE2CSV](https://github.com/MarkBaggett/ese-analyst)  

<br>
### Escape Ed - Terminal Challenge

|    |       |
|----|-------|
|Elf Name|Bushy Evergreen|
|Pre-Solve Hints|[ed Editor Basics](http://cs.wellesley.edu/~cs249/Resources/ed_is_the_standard_text_editor.html)|
|Post-Solve Hints| [Deep Blue CLI Posting](https://www.ericconrad.com/2016/09/deepbluecli-powershell-module-for-hunt.html), [Deep Blue CLI on Github](https://github.com/sans-blue-team/DeepBlueCLI) |
|Objective||

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image13.PNG"
     alt="">
    <br>
    Kringlecon 2 - Escape Ed - Terminal Challenge
</div><br>  

After you read the ed Editor Basics you find the solution for this terminal challenge.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image14.PNG"
     alt="">
    <br>
    Kringlecon 2 - Escape Ed - Terminal Challenge
</div><br>


#### Escape Ed - Solution:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image15.PNG"
     alt="">
    <br>
    Kringlecon 2 - Escape Ed - Terminal Challenge
</div><br>

Answer:
```Solution:
Press q and press Enter.
```

Message from Bushy Evergreen after solving the challenge:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image16.PNG"
     alt="">
    <br>
    Kringlecon 2 - Objective 3 Hint
</div><br>

<br>
### Objective 3 - Walkthrough

After you solve the terminal challenge, you learn about Deep Blue CLI.

You download Deep Blue CLI and run it against the 'security.evtx' file for the challenge.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image17.PNG"
     alt="">
    <br>
    Deep Blue CLI - Partial result of '.\DeepBlue.ps1 .\Security.evtx '
</div><br>

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image18.PNG"
     alt="">
    <br>
    Deep Blue CLI - Partial result of '.\DeepBlue.ps1 .\Security.evtx '
</div><br>

When you view the Total Logon Failures, you quickly notice that all except one account have '77' failures. This may indicate that the account was authenticated successfully on the 77th attempt.
<br>
#### Objective 3 - Solution
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image19.PNG"
     alt="">
    <br>
    Deep Blue CLI - Partial result of '.\DeepBlue.ps1 .\Security.evtx '
</div><br>

Answer:
```
supatree
```

---
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div><br>

## Objective 4 - Windows Log Analysis: Determine Attacker Technique

|    |       |
|----|-------|
|Inspirational Quote| "Go Hack it!" -kaknowles |
|Objective|Using these normalized Sysmon logs, identify the tool the attacker used to retrieve domain password hashes from the lsass.exe process. For hints on achieving this objective, please visit Hermey Hall and talk with SugarPlum Mary.|
|Difficulty Level:|2|
|Links| [sysmon-data.json.zip](https://downloads.elfu.org/sysmon-data.json.zip)|  
|Related Video|[]()|


<br>
### Linux Path - Terminal Challenge

|    |       |
|----|-------|
|Elf Name|SugarPlum Mary|
|Pre-Solve Hints|Green words matter, files must be found, and the terminal's $PATH matters.|
|Post-Solve Hints| [EQL Threat Hunting](https://pen-testing.sans.org/blog/2019/12/10/eql-threat-hunting/), [Sysmon By Carlos Perez](https://www.darkoperator.com/blog/2014/8/8/sysinternals-sysmon) |
|Objective||

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image20.PNG"
     alt="">
    <br>
    Kringlecon 2 - Linux Path
</div><br>  

You open the terminal.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image21.PNG"
     alt="">
    <br>
    Kringlecon 2 - Linux Path Terminal
</div><br>  

The objective is to get a listing of the current directory. You try the obvious solutions.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image23.PNG"
     alt="">
    <br>
    Kringlecon 2 - 'ls' and 'dir'
</div><br>  


You remember the objective mentions that green words matter.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image24.PNG"
     alt="">
    <br>
    Kringlecon 2 - which ls
</div><br>  

You try to find other programs that start with 'ls' .
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image22.PNG"
     alt="">
    <br>
    Kringlecon 2 - locate '/ls/
</div><br>  

You check the Path.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image25.PNG"
     alt="">
    <br>
    Kringlecon 2 - echo $PATH
</div><br>  

You run '/bin/ls' to get dir listing.
<br>
#### Linux Path - Solution:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image27.PNG"
     alt="">
    <br>
    Kringlecon 2 - '/bin/ls'
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image28.PNG"
     alt="">
    <br>
    Kringlecon 2 - 'rejected-elfu-logos.txt'
</div><br>  

Answer:
```
/bin/ls
```

Message from SugarPlum Mary after solving the challenge:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image29.PNG"
     alt="">
    <br>
    Kringlecon 2 - 'rejected-elfu-logos.txt'
</div><br>  

<br>
### Objective 4 - Walkthrough
You read the hints provided by SugarPlum Mary. You run the following three queries to solve this challenge:

Query 1:
```
$ eql query -f sysmon-data.json "process where process_name = 'lsass.exe'"
```

Query 1 gives you no results. You continue your journey with query 2.

Query 2:
```
$ eql query -f sysmon-data.json "process where parent_process_name = 'lsass.exe'" > results.json
```

You receive the following results from Query 2:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image30.PNG"
     alt="">
    <br>
    Kringlecon 2 - Query 2 results
</div><br>  

You pivot on PID and run Query 3.

Query 3:
```
eql query -f sysmon-data.json "process where ppid = 3440" > results.json
```

You get the following result:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image31.PNG"
     alt="">
    <br>
    Kringlecon 2 - Query 3 results
</div><br>  

<br>
#### Objective 4 - Solution
Answer:
```
ntdsutil
```

---
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div><br>

## Objective 5 - Network Log Analysis: Determine Compromised System

|    |       |
|----|-------|
|Inspirational Quote| "Tackle problems one step at a time. Take regular cocoa breaks!!" - kaknowles|
|Objective|The attacks don't stop! Can you help identify the IP address of the malware-infected system using these Zeek logs? For hints on achieving this objective, please visit the Laboratory and talk with Sparkle Redberry.|
|Difficulty Level:|2|
|Links| [Zeek logs](https://downloads.elfu.org/elfu-zeeklogs.zip)|  
|Related Video|[John Strand, Keynote: A Hunting We Must Go](https://www.youtube.com/watch?v=jxOZ5u2CYWw&list=PLjLd1hNA7YVzyhhqBQaW-tF45xnS6oHAP&index=2)|


<br>
### Xmas Cheer Laser - Terminal Challenge

|    |       |
|----|-------|
|Elf Name|Sparkle Redberry|
|Pre-Solve Hints|[SANS' PowerShell Cheat Sheet](https://blogs.sans.org/pen-testing/files/2016/05/PowerShellCheatSheet_v41.pdf)|
|Post-Solve Hints| [RITA's homepage](https://www.activecountermeasures.com/free-tools/rita/)|
|Objective||

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image33.PNG"
     alt="">
    <br>
    Kringlecon 2 - Xmas Cheer Laser - Terminal Challenge
</div><br>  

You load the terminal for this challenge.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image34.PNG"
     alt="">
    <br>
    Kringlecon 2 - Xmas Cheer Laser - Terminal Challenge
</div><br>  

You run the command ```(Invoke-WebRequest -Uri http://localhost:1225/).RawContent ``` for more info.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image35.PNG"
     alt="">
    <br>
    Kringlecon 2 - Invoke-WebRequest -Uri http://localhost:1225/).RawContent
</div><br>  

You do a directory listing to see what files are in the current directory. You read the callingcard.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image36.PNG"
     alt="">
    <br>
    Kringlecon 2 - Callingcard.txt
</div><br>  

The calling card has references to history. You view the history.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image37.PNG"
     alt="">
    <br>
    Kringlecon 2 - 'history'
</div><br>  

You notice Item 7 and 9 in history looks interesting.

You make a note of Item 7, ```(Invoke-WebRequest -Uri http://localhost:1225/api/angle?val=65.5).RawContent```.

You're unable to read all of item 9, you dump history with all the properties.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image41.PNG"
     alt="">
    <br>
    Kringlecon 2 - riddle in history
</div><br>  

You ponder on the riddle in the history item for a little while... You realize the riddle is referring to environment variables. You view the environment variables in the terminal.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image42.PNG"
     alt="">
    <br>
    Kringlecon 2 - Environment variables
</div><br>  

You notice an environment variable named 'riddle'. You can't view the full content of the variable. You use ```out-string width 4096``` to view more. You view the content of this environment variable.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image43.PNG"
     alt="">
    <br>
    Kringlecon 2 - Environment variables expanded
</div><br>  

You compose a command line to search /etc recursively to look for the newest file that is likely compressed.

```
get-childitem -Path /etc –recurse -ErrorAction SilentlyContinue |  where-object {$_.lastwritetime -gt (get-date).addDays(-1)} |  where-object {-not $_.PSIsContainer} | Foreach-Object { $_.FullName + " " + $_.lastwritetime}
```

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image44.PNG"
     alt="">
    <br>
    Kringlecon 2 - Riddle solution
</div><br>  

You expand the 'archive' file using the command ```Expand-Archive -LiteralPath /etc/apt/archive -DestinationPath /home/elf/archive```.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image45.PNG"
     alt="">
    <br>
    Kringlecon 2 - Expanding 'archive' file
</div><br>  

You examine the content.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image46.PNG"
     alt="">
    <br>
    Kringlecon 2 - dir 'archive' file
</div><br>  


<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image47.PNG"
     alt="">
    <br>
    Kringlecon 2 - dir 'archive' file
</div><br>  

You find two files, another riddle and ```runme.elf```.

You read the riddle.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image48.PNG"
     alt="">
    <br>
    Kringlecon 2 - riddle in 'archive' file
</div><br>  

You have difficulty running the ```runme.elf```. You google how to run elf file, you find the following article:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image57.PNG"
     alt="">
    <br>
    Kringlecon 2 - how to run 'elf' file
</div><br>  

You try changing the attribute of the file prior to running it.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image58.PNG"
     alt="">
    <br>
    Kringlecon 2 - 'runme.elf'
</div><br>  

You make a note of the refraction value.

You use the following powershell command to find a file with the specified md5 hash.

```Get-ChildItem /home/elf -File -Recurse | Select DirectoryName,Name,@{N='Version';E={$_.VersionInfo.ProductVersion}},LastWriteTime,Length,@{N='FileHash';E={(Get-FileHash -Algorithm MD5 $_).Hash}} | select-string "25520151A320B5B0D21561F92C8F6224"```

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image49.PNG"
     alt="">
    <br>
    Kringlecon 2 - File with MD5 hash "25520151A320B5B0D21561F92C8F6224"
</div><br>  

You view this file.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image50.PNG"
     alt="">
    <br>
    Kringlecon 2 - Another riddle
</div><br>  

You make a note of the temperature. You find another riddle in this file.

You create the following powershell command to solve the riddle:

```
get-childitem -Path /home/elf/depths/ –recurse -ErrorAction SilentlyContinue  | Foreach-Object { $_.FullName } | sort { $_.length } |
```

The results are as follow:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image51.PNG"
     alt="">
    <br>
    Kringlecon 2 - Riddle solution
</div><br>  


<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image52.PNG"
     alt="">
    <br>
    Kringlecon 2 - Yet another riddle.
</div><br>  

You use the following powershell command to solve the above riddle.

```
Get-Process -IncludeUserName | Select-Object Id,Name,Username,Path
Stop-Process -ID 23 -Force
Stop-Process -ID 26 -Force
Stop-Process -ID 27 -Force
Stop-Process -ID 29 -Force
```

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image53.PNG"
     alt="">
    <br>
    Kringlecon 2 - Yet another riddle.
</div><br>  

You do a dir listing of ```/shall``` to find another riddle. You use the following powershell command to solve this riddle.

```
get-childitem -Path /etc *.xml –recurse -ErrorAction SilentlyContinue
```

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image54.PNG"
     alt="">
    <br>
    Kringlecon 2 - Riddle solution
</div><br>  

You ponder on how to this. After a while you try the following command:

```
type /etc/systemd/system/timers.target.wants/EventLog.xml | Select-String "<I32 N=""Id"">" | Group-Object
```

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image55.PNG"
     alt="">
    <br>
    Kringlecon 2 - lonely event id
</div><br>  

You use the following powershell command to get the properties of the lonely event id.

```
type /etc/systemd/system/timers.target.wants/EventLog.xml | Select-String "<I32 N=""Id"">1</I32>" -Context 1,150
```

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image56.PNG"
     alt="">
    <br>
    Kringlecon 2 -'$correct_gases_postbody'
</div><br>  

You make a note of the correct gases.

Now you have the temperature, angle, gas composition, refraction value. You set the correct parameters on the laser.



<br>
#### Xmas Cheer Laser - Solution:
Answer:
``` powershell
(Invoke-WebRequest -Uri http://localhost:1225/api/off).RawContent
(Invoke-WebRequest -Uri http://localhost:1225/api/refraction?val=1.867).RawContent
(Invoke-WebRequest -Uri http://localhost:1225/api/temperature?val=-33.5).RawContent
(Invoke-WebRequest -Uri http://localhost:1225/api/angle?val=65.5).RawContent
$correct_gases_postbody = "O=6&H=7&He=3&N=4&Ne=22&Ar=11&Xe=10&F=20&Kr=8&Rn=9"
Invoke-WebRequest -Uri http://localhost:1225/api/gas -Method POST -Body $correct_gases_postbody
(Invoke-WebRequest -Uri http://localhost:1225/api/on).RawContent
```
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image59.PNG"
     alt="">
    <br>
    Xmas Cheer Laser - Solution
</div><br>  


Message from Sparkle Redberry after solving the challenge:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image60.PNG"
     alt="">
    <br>
    Xmas Cheer Laser - Solution
</div><br>  



<br>
### Objective 5 - Walkthrough
You read the Rita hint from the terminal challenge and watch the related video. You're now a RITA expert!

You extract the Zeek files provided in this challenge. You view the RITA output.

You view the Beacons:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image61.PNG"
     alt="">
    <br>
    RITA - Beacons
</div><br>  

<br>
#### Objective 5 - Solution
Answer:
```
144.202.46.214
```

---
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div><br>

## Objective 6 - Splunk

|    |       |
|----|-------|
|Inspirational Quote| "Set boundaries (time, abuse, triggers, requests, pancakes...)" -hacks4pancake |
|Objective|Access https://splunk.elfu.org/ as elf with password elfsocks. What was the message for Kent that the adversary embedded in this attack? The SOC folks at that link will help you along! For hints on achieving this objective, please visit the Laboratory in Hermey Hall and talk with Prof. Banas.|
|Difficulty Level:|3|
|Links| [https://splunk.elfu.org/](https://splunk.elfu.org/)|  
|Related Video|[James Brodsky, Dashing Through the Logs](https://www.youtube.com/watch?v=qbIhHhRKQCw&list=PLjLd1hNA7YVzyhhqBQaW-tF45xnS6oHAP)|


<br>
### Splunk Training Questions - Terminal Challenge

|    |       |
|----|-------|
|Elf Name|Professor Banas|
|Objective||

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image62.PNG"
     alt="">
    <br>
    Kringlecon 2 - Splunk Training
</div><br>  

You proceed to login to ```https://splunk.elfu.org/ wither username elf/Password:elfsocks```.

Once you log in, you're greeted with the following messages:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image63.PNG"
     alt="">
    <br>
    Kringlecon 2 - https://splunk.elfu.org/ welcome page
</div><br>  


<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image64.PNG"
     alt="">
    <br>
    Kringlecon 2 - https://splunk.elfu.org/ ELF University SOC
</div><br>  

The various Chats will help you answer the training questions and the challenge questions.

Here is the list of the questions:

```
Question 1:  
What is the short host name of Professor Banas' computer?

Question 2:  
What is the name of the sensitive file that was likely accessed and copied by the attacker? Please provide the fully qualified location of the file. (Example: C:\temp\report.pdf)		

Question 3:  
What is the fully-qualified domain name(FQDN) of the command and control(C2) server? (Example: badguy.baddies.com)		

Question 4:
What document is involved with launching the malicious PowerShell code? Please provide just the filename. (Example: results.txt)		

Question 5:
How many unique email addresses were used to send Holiday Cheer essays to Professor Banas? Please provide the numeric value. (Example: 1)		

Question 6:
What was the password for the zip archive that contained the suspicious file?		
```

You work with the users in SOC to answer these questions. They walk you through answering each question. You read the chat and perform the searches, review the results to answer the questions.

For question 1 you review ```#ELFU SOC``` chat log.  
For question 2, you search ```index=main santa``` and review the results.  
For question 3, you search for ```index=main sourcetype=XmlWinEventLog:Microsoft-Windows-Sysmon/Operational powershell EventCode=3```  
For question 4, you search for ```index=main sourcetype=WinEventLog EventCode=4688 | reverse``` and review the events.  
For question 5, you search for ```index=main sourcetype=stoq | table _time results{}.workers.smtp.to results{}.workers.smtp.from  results{}.workers.smtp.subject results{}.workers.smtp.body | search results{}.workers.smtp.subject="*Holiday
 Cheer Assignment Submission*" results{}.workers.smtp.to="*carl*"```  
For question 6, you can find the password in the malicious email carl received in question 5.

<br>
#### Splunk Training Questions - Solution:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image73.PNG"
     alt="">
    <br>
    Kringlecon 2 - Training Questions/Answers
</div><br>  

Answer:
```
Training Questions
1. sweetums
2. C:\Users\cbanas\Documents\Naughty_and_Nice_2019_draft.txt
3. 144.202.46.214.vultr.com
4. 19th Century Holiday Cheer Assignment.docm
5. 21
6. 123456789
7. Bradly.Buttercups@eIfu.org
```


<br>
### Objective 6 - Walkthrough
```
Challenge Question:
What was the message for Kent that the adversary embedded in this attack?
```
Alice Bluebeard assists you with this challenge. Here is a list of files of interest:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image76.PNG"
     alt="">
    <br>
    Kringlecon 2 - List of interesting files
</div><br>  


You will use the following splunk search get a list of files that may contain the message for Kent:

```
index=main sourcetype=stoq  "results{}.workers.smtp.from"="bradly buttercups <bradly.buttercups@eifu.org>"
| eval results = spath(_raw, "results{}")
| mvexpand results
| eval path=spath(results, "archivers.filedir.path"), filename=spath(results, "payload_meta.extra_data.filename"), fullpath=path."/".filename
| search fullpath!=""
| table filename,fullpath
```

You will get the following results:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image75.PNG"
     alt="">
    <br>
    Kringlecon 2 - Files
</div><br>  

Looking at the malicious file you get the following message:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image77.PNG"
     alt="">
    <br>
    Kringlecon 2 - malicious file
</div><br>  

You try a different file and see the following:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image78.PNG"
     alt="">
    <br>
    Kringlecon 2 - xml file
</div><br>  

<br>
#### Objective 6 - Solution

Answer:
```
Kent you are so unfair. And we were going to make you the king of the Winter Carnival.
```

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image74.PNG"
     alt="">
    <br>
    Kringlecon 2 - Challenge Answer
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image79.PNG"
     alt="">
    <br>
    Kringlecon 2 - Challenge Answer
</div><br>  

---
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div><br>

## Objective 7 - Get Access To The Steam Tunnels

|    |       |
|----|-------|
|Inspirational Quote| "Deep breath, Loook at the data!" - Random Math Professor standing behind you |
|Objective|Gain access to the steam tunnels. Who took the turtle doves? Please tell us their first and last name. For hints on achieving this objective, please visit Minty's dorm room and talk with Minty Candy Cane.|
|Difficulty Level:|3|
|Links| [Key Decoding](https://github.com/deviantollam/decoding/tree/master/Key%20Decoding)|  
|Related Video|[Deviant Ollam, Optical Decoding of Keys](https://www.youtube.com/watch?v=KU6FJnbkeLA&list=PLjLd1hNA7YVzyhhqBQaW-tF45xnS6oHAP)|


Prior to accessing the terminal challenge we need to unlock the dorm room.
<br>
### Frosty Keypad Challenge
Here is the keypad to access the dorm room:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image80.PNG"
     alt="">
    <br>
    Kringlecon 2 - Frosty Keypad
</div><br>  

The Elf Tangle Coalbox by the dorm door gives you the following hints:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image81.PNG"
     alt="">
    <br>
    Kringlecon 2 - Elf Tangle Coalbox
</div><br>  


<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image82.PNG"
     alt="">
    <br>
    Kringlecon 2 - Frosty Keypad Hints
</div><br>  

From the keypad and the hints you can tell the three keys in the code are '1', '3' and '7'.

You write the following python function to find all the 4 digit prime numbers with only the digits '1', '3', '7'.

``` python
# prime function from https://stackoverflow.com/questions/15285534/isprime-function-for-python-language
def is_prime(n):
  if n == 2 or n == 3: return True
  if n < 2 or n%2 == 0: return False
  if n < 9: return True
  if n%3 == 0: return False
  r = int(n**0.5)
  f = 5
  while f <= r:
    #print ('\t',f)
    if n%f == 0: return False
    if n%(f+2) == 0: return False
    f +=6
  return True    


# Program to check if a number is prime or not

# for number in range(1000:10000)

for number in range(1000,10000):

        x = str(number)
        #print(x + ' is Prime.')
        if (x.find('1')>-1 and x.find('3')>-1 and x.find('7')>-1):
            if (x.find('0')== -1 and x.find('2')== -1 and x.find('4')== -1 and x.find('5')== -1 and x.find('6')== -1  and x.find('8')== -1 and x.find('9')== -1):    
                if is_prime(number):
                    print(x + ' is Prime.')
```

Here are the result of the above program:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image84.PNG"
     alt="">
    <br>
    Kringlecon 2 - Frosty Keypad Possible Combinations
</div><br>  

#### Frosty Keypad - Solution

You try all the above combinations and find the correct combination is ```7331```. Once you enter the dorm room, you notice that the combination is written on the wall.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image85.PNG"
     alt="">
    <br>
    Kringlecon 2 - Dorm Room - Bad Security
</div><br>



### Holiday Hack Trial - Terminal Challenge

|    |       |
|----|-------|
|Elf Name|Misty CandyCane|
|Pre-Solve Hints|[Web Apps: A Trailhead](https://youtu.be/0T6-DQtzCgM)|
|Post-Solve Hints| [Deviant's Key Decoding Templates](https://github.com/deviantollam/decoding),[Optical Decoding of Keys](https://youtu.be/KU6FJnbkeLA) |
|Objective||

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image87.PNG"
     alt="">
    <br>
    Kringlecon 2 - Minty Candycane
</div><br>  

The game has 3 difficulty levels. You notice a URL on top of the game page.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image88.PNG"
     alt="">
    <br>
    Kringlecon 2 - Holiday Hack Trail - Terminal Challenge
</div><br>  

#### Easy mode
You select the EASY mode. You notice the URL on top of the game has changed.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image89.PNG"
     alt="">
    <br>
    Kringlecon 2 - Easy mode
</div><br>  

You copy and paste the URI to a text editor:

```
hhc://trail.hhc/trail/?difficulty=0&distance=0&money=3600&pace=0&curmonth=7&curday=1&reindeer=4&runners=4&ammo=100&meds=20&food=400&name0=Anna&health0=100&cond0=0&causeofdeath0=&deathday0=0&deathmonth0=0&name1=Michael&health1=100&cond1=0&causeofdeath1=&deathday1=0&deathmonth1=0&name2=Billy&health2=100&cond2=0&causeofdeath2=&deathday2=0&deathmonth2=0&name3=Vlad&health3=100&cond3=0&causeofdeath3=&deathday3=0&deathmonth3=0
```

You update the distance variable in the URL to 8000 and press the ```>```.

You press the Go button and you get the following message:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image90.PNG"
     alt="">
    <br>
    Kringlecon 2 - Terminal Challenge Solved
</div><br>  

#### Medium mode
You start the game again on Medium difficulty. You notice the URL bar has changed. You no longer can modify the variables in the URL to win.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image92.PNG"
     alt="">
    <br>
    Kringlecon 2 - Medium mode
</div><br>  

You inspect the elements on the page and find a div 'statusContainer' that contains hidden variables.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image93.PNG"
     alt="">
    <br>
    Kringlecon 2 - statusContainer
</div><br>  

You modify the distance variable to 8000 and press "Go".
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image94.PNG"
     alt="">
    <br>
    Kringlecon 2 - distance variable
</div><br>  


#### Hard mode
You start the game in hard difficulty mode.

The solutions for the last two mode no longer work. You examine the 'statusContainer and notice now it contains a hash value.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image95.PNG"
     alt="">
    <br>
    Kringlecon 2 - hash
</div><br>  

You type the hash in [Crackstation](https://crackstation.net/).

You get the following result:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image96.PNG"
     alt="">
    <br>
    Kringlecon 2 - md5 hash
</div><br>  

The hash ```6da9003b743b65f4c0ccd295cc484e57``` is a md5 hash for ```230```.

After playing around with the game for a while, you notice the hash is calculated by adding all the values together.
The Values added are money, distance, curmonth, curday, runners,reindeer, ammo, meds, food.

You restart the game. You add calculate the md5 hash of (8000+230).  You use [CyberChef](https://gchq.github.io/CyberChef/) to calculate the hash.  The hash is ```bd4a6d0563e0604510989eb8f9ff71f5```

You update the distance to 8000 and hash to the above and press ```Go```.


<br>
#### Holiday Hack Trial - Solution:
Answer:
```
Easy:

hhc://trail.hhc/trail/?difficulty=0&distance=8000&money=3600&pace=0&curmonth=7&curday=1&reindeer=4&runners=4&ammo=100&meds=20&food=400&name0=Anna&health0=100&cond0=0&causeofdeath0=&deathday0=0&deathmonth0=0&name1=Michael&health1=100&cond1=0&causeofdeath1=&deathday1=0&deathmonth1=0&name2=Billy&health2=100&cond2=0&causeofdeath2=&deathday2=0&deathmonth2=0&name3=Vlad&health3=100&cond3=0&causeofdeath3=&deathday3=0&deathmonth3=0

Medium:
Modify the distance variable in div "statusContainer" to 8000 and press "Go".

Hard:
You use the same solution as Medium, except you update the hash.
The hash is md5(sum(money, distance, curmonth, curday, runners,reindeer, ammo, meds, food))

```

Message from Minty Candycane after solving the challenge:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image91.PNG"
     alt="">
    <br>
    Kringlecon 2 - Minty Candycane - Terminal Challenge
</div><br>  

<br>
### Objective 7 - Walkthrough
You watch the video for this challenge. You review the elements on the page and notice a class called "krampus scampering".


<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image97.PNG"
     alt="">
    <br>
    Kringlecon 2 - "krampus scampering"
</div><br>  

You open the [image](https://2019.kringlecon.com/images/avatars/elves/krampus.png) mentioned in the krampus class in your browser.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image98.png"
     alt="">
    <br>
    Kringlecon 2 - krampus.png
</div><br>  


You cut the key image and rotate it.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image99.png"
     alt="">
    <br>
    Kringlecon 2 - krampus's key
</div><br>  

You have two options, use the templates provided for the challange or try to eyeball it.

You decide to eyeball it.

You trying the following combinations

```
133430
133530
133630
133730
233530
122420
122520(answer)
```

The door opens up with ```122520``` key.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image100.PNG"
     alt="">
    <br>
    Kringlecon 2 - Door opened by key `122520`
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image101.png"
     alt="">
    <br>
    Kringlecon 2 - Key `122520`
</div><br>  

You through the door and down the steam tunnel. You reach the end of the steam tunnel.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image102.png"
     alt="">
    <br>
    Kringlecon 2 - Krampus / Frido Sleigh Contest
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image103.PNG"
     alt="">
    <br>
    Kringlecon 2 - Krampus Hollyfeld
</div><br>  


<br>
#### Objective 7 - Solution
Answer:
```
Krampus Hollyfeld
```

---
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div><br>

## Objective 8 - Bypassing the Frido Sleigh CAPTEHA

|    |       |
|----|-------|
|Inspirational Quote| "Being devious is half of the fun!" -kaknowles |
|Objective|Help Krampus beat the Frido Sleigh contest. For hints on achieving this objective, please talk with Alabaster Snowball in the Speaker Unpreparedness Room.|
|Difficulty Level:|4|
|Links| [Frido Sleigh contest](https://fridosleigh.com/), [12,000 images](https://downloads.elfu.org/capteha_images.tar.gz), [API interface ](https://downloads.elfu.org/capteha_api.py)|  
|Related Video|[Chris Davis, Machine Learning Use Cases for Cybersecurity](https://www.youtube.com/watch?v=jmVPLwjm_zs) |

<br>
###  Nyanshell - Terminal Challenge

|    |       |
|----|-------|
|Elf Name|Alabaster Snowball|
|Pre-Solve Hints| On Linux, a user's shell is determined by the contents of /etc/passwd, sudo -l says I can run a command as root. What does it do?|
|Post-Solve Hints|[Chris Davis, Machine Learning Use Cases for Cybersecurity](https://www.youtube.com/watch?v=jmVPLwjm_zs) |
|Objective||

You arrive in the Speaker Unpreparedness Room.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image113.PNG"
     alt="">
    <br>
    Kringlecon 2 - Speaker Unpreparedness Room
</div><br>  

You talk to Alabaster Snowball.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image104.PNG"
     alt="">
    <br>
    Kringlecon 2 - Alabaster Snowball - Terminal Challenge
</div><br>  

You open the Nyanshell.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image105.PNG"
     alt="">
    <br>
    Kringlecon 2 - Nyanshell - Terminal Challenge
</div><br>  

You run ```sudo -l``` to see the list of files you can and can't run with sudo permission.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image106.PNG"
     alt="">
    <br>
    Kringlecon 2 - sudo -l
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image107.PNG"
     alt="">
    <br>
    Kringlecon 2 - /etc/passwd
</div><br>  

You look around in different folders, and you find a file /```entrypoint.sh```
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image108.PNG"
     alt="">
    <br>
    Kringlecon 2 - entrypoint.sh
</div><br>

You try running ```entrypoint.sh```. You check the attribute of ```/bin/nsh``` using ```lsattr /bin/nsh``` command. You notice ```/bin/nsh``` is marked as immutable.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image109.PNG"
     alt="">
    <br>
    Kringlecon 2 - getting attribute of /bin/nsh
</div><br>

You change this attribute by using ```sudo chattr -i /bin/nsh``` command. You copy ```/bin/bash``` over ```/bin/nsh```

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image110.PNG"
     alt="">
    <br>
    Kringlecon 2 - changing nsh from immutable to mutable
</div><br>

You login as alabaster_snowball with the username provided on loading of the terminal (alabaster_snowball/Password2).

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image111.PNG"
     alt="">
    <br>
    Kringlecon 2 - su alabaster_snowball
</div><br>

You run the success script after.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image112.PNG"
     alt="">
    <br>
    Kringlecon 2 - running the success script
</div><br>

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image114.PNG"
     alt="">
    <br>
    Kringlecon 2 - nyancat
</div><br>


####  Nyanshell - Solution:
Answer:
```
sudo chattr -i /bin/nsh
cp /bin/bash /bin/nsh
su alabaster_snowball with password: "Password2"
```

Message from Alabaster Snowball after solving the challenge:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image115.PNG"
     alt="">
    <br>
    Kringlecon 2 - Nyanshell solved
</div><br>

### Objective 8 - Walkthrough
You view the website for the contest, [Frido Sleigh contest](https://fridosleigh.com/). The website has a complex captcha puzzle.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image116.PNG"
     alt="">
    <br>
    Kringlecon 2 - Contest Captcha
</div><br>

You watch the related video for this objective. You download all the related files for this section.

- [12,000 images](https://downloads.elfu.org/capteha_images.tar.gz)
- [API interface ](https://downloads.elfu.org/capteha_api.py)


You download the repository from the video [img_rec_tf_ml_demo](https://github.com/chrisjd20/img_rec_tf_ml_Demo).

You follow the instructions on the img_rec_tf_ml_demo github page to install Tensorflow:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image117.PNG"
     alt="">
    <br>
    Kringlecon 2 - TensorFlow installation
</div><br>

You run the demo to ensure you get the coprrect results.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image118.PNG"
     alt="">
    <br>
    Kringlecon 2 - TensorFlow Demo
</div><br>


You download capteha_api.py file and copy it to the demo tensorflow folder.

You extract the 12,000 images you downloaded by running the following commands:

```
mkdir training_images
tar xvzf capteha_images.tar.gz -C ./training_images
```

You remove the demo model training files, ```rm -r /tmp/retrain_tmp/```.

You retrain with model with the capteha_images.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image120.PNG"
     alt="">
    <br>
    Kringlecon 2 - Training Model 1/2
</div><br>


<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image121.PNG"
     alt="">
    <br>
    Kringlecon 2 - Training Model 2/2
</div><br>



You review ```capteha_api.py``` and ```predict_images_using_trained_model.py``` from the tensorflow demo.

You add ```capteha_api.py``` to ```predict_images_using_trained_model.py``` file.

You write the code the extra code to use ML model to solve the captcha.

``` python
#!/usr/bin/python3
# Image Recognition Using Tensorflow Exmaple.
# Code based on example at:
# https://raw.githubusercontent.com/tensorflow/tensorflow/master/tensorflow/examples/label_image/label_image.py
import os
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '3'
import tensorflow as tf
tf.logging.set_verbosity(tf.logging.ERROR)
import numpy as np
import threading
import queue
import time
import sys
import requests
import json
import base64
from array import *

# sudo apt install python3-pip
# sudo python3 -m pip install --upgrade pip
# sudo python3 -m pip install --upgrade setuptools
# sudo python3 -m pip install --upgrade tensorflow==1.15

def load_labels(label_file):
    label = []
    proto_as_ascii_lines = tf.gfile.GFile(label_file).readlines()
    for l in proto_as_ascii_lines:
        label.append(l.rstrip())
    return label

def predict_image(q, sess, graph, image_bytes, img_full_path, labels, input_operation, output_operation):
    image = read_tensor_from_image_bytes(image_bytes)
    results = sess.run(output_operation.outputs[0], {
        input_operation.outputs[0]: image
    })
    results = np.squeeze(results)
    prediction = results.argsort()[-5:][::-1][0]
    q.put( {'img_full_path':img_full_path, 'prediction':labels[prediction].title(), 'percent':results[prediction]} )

def load_graph(model_file):
    graph = tf.Graph()
    graph_def = tf.GraphDef()
    with open(model_file, "rb") as f:
        graph_def.ParseFromString(f.read())
    with graph.as_default():
        tf.import_graph_def(graph_def)
    return graph

def read_tensor_from_image_bytes(imagebytes, input_height=299, input_width=299, input_mean=0, input_std=255):
    image_reader = tf.image.decode_png( imagebytes, channels=3, name="png_reader")
    float_caster = tf.cast(image_reader, tf.float32)
    dims_expander = tf.expand_dims(float_caster, 0)
    resized = tf.image.resize_bilinear(dims_expander, [input_height, input_width])
    normalized = tf.divide(tf.subtract(resized, [input_mean]), [input_std])
    sess = tf.compat.v1.Session()
    result = sess.run(normalized)
    return result

def main():
    # Loading the Trained Machine Learning Model created from running retrain.py on the training_images directory
    graph = load_graph('/tmp/retrain_tmp/output_graph.pb')
    labels = load_labels("/tmp/retrain_tmp/output_labels.txt")

    # Load up our session
    input_operation = graph.get_operation_by_name("import/Placeholder")
    output_operation = graph.get_operation_by_name("import/final_result")
    sess = tf.compat.v1.Session(graph=graph)

    ### capteha_api.py
    #yourREALemailAddress = "YourRealEmail@SomeRealEmailDomain.RealTLD"
    yourREALemailAddress = "mo@.SomeRealEmailDomain.RealTLD.org"

    # Creating a session to handle cookies
    s = requests.Session()
    url = "https://fridosleigh.com/"
    print("Sending capteha request...")
    json_resp = json.loads(s.get("{}api/capteha/request".format(url)).text)
    b64_images = json_resp['images']                    # A list of dictionaries eaching containing the keys 'base64' and 'uuid'
    challenge_image_type = json_resp['select_type'].split(',')     # The Image types the CAPTEHA Challenge is looking for.
    challenge_image_types = [challenge_image_type[0].strip(), challenge_image_type[1].strip(), challenge_image_type[2].replace(' and ','').strip()] # cleaning and formatting

    print("Challenge types:" + str(challenge_image_types))


    # Can use queues and threading to spead up the processing
    q = queue.Queue()
    unknown_images_dir = 'unknown_images'
    unknown_images = os.listdir(unknown_images_dir)

    #Going to interate over each of our images.
    #for image in unknown_images:
    for image in b64_images:
        print("img uuid:" + str(image['uuid']))
        # https://stackoverflow.com/questions/16214190/how-to-convert-base64-string-to-image
        imgdata = base64.b64decode(image['base64'])

        #img_full_path = '{}/{}'.format(unknown_images_dir, image)

        #print('Processing Image {}'.format(img_full_path))
        # We don't want to process too many images at once. 10 threads max
        while len(threading.enumerate()) > 10:
            time.sleep(0.0001)

        #predict_image function is expecting png image bytes so we read image as 'rb' to get a bytes object
        #image_bytes = open(img_full_path,'rb').read()
        image_bytes = imgdata
        #threading.Thread(target=predict_image, args=(q, sess, graph, image_bytes, img_full_path, labels, input_operation, output_operation)).start()
        threading.Thread(target=predict_image, args=(q, sess, graph, image_bytes, str(image['uuid']), labels, input_operation, output_operation)).start()

    print('Waiting For Threads to Finish...')
    while q.qsize() < len(b64_images):
        time.sleep(0.001)

    #getting a list of all threads returned results
    prediction_results = [q.get() for x in range(q.qsize())]
    final_answer = ""
    #do something with our results... Like print them to the screen.
    for prediction in prediction_results:

        if any(image_type in str(prediction["prediction"]) for image_type in challenge_image_types):
            final_answer = final_answer + str(prediction["img_full_path"]) + ","
            print (str(prediction))
            print('TensorFlow Predicted {img_full_path} is a {prediction} with {percent:.2%} Accuracy'.format(**prediction) + str(challenge_image_types))


    ### capteha_api.py

    final_answer = final_answer.rstrip(',')
    print("final answer:" + final_answer)

    # This should be JUST a csv list image uuids ML predicted to match the challenge_image_type .
    #final_answer = ','.join( [ img['uuid'] for img in b64_images ] )

    json_resp = json.loads(s.post("{}api/capteha/submit".format(url), data={'answer':final_answer}).text)
    if not json_resp['request']:
        # If it fails just run again. ML might get one wrong occasionally
        print('FAILED MACHINE LEARNING GUESS')
        print('--------------------\nOur ML Guess:\n--------------------\n{}'.format(final_answer))
        print('--------------------\nServer Response:\n--------------------\n{}'.format(json_resp['data']))
        sys.exit(1)


    print('CAPTEHA Solved!')
    # If we get to here, we are successful and can submit a bunch of entries till we win
    userinfo = {
        'name':'Krampus Hollyfeld',
        'email':yourREALemailAddress,
        'age':180,
        'about':"Cause they're so flippin yummy!",
        'favorites':'thickmints'
    }
    # If we win the once-per minute drawing, it will tell us we were emailed.
    # Should be no more than 200 times before we win. If more, somethings wrong.
    entry_response = ''
    entry_count = 1
    while yourREALemailAddress not in entry_response and entry_count < 200:
        print('Submitting lots of entries until we win the contest! Entry #{}'.format(entry_count))
        entry_response = s.post("{}api/entry".format(url), data=userinfo).text
        entry_count += 1
    print(entry_response)



if __name__ == "__main__":
    main()

```

You run the combined code, you get the following results:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image122.PNG"
     alt="">
    <br>
    Kringlecon 2 - Solving CAPTEHA
</div><br>

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image124.PNG"
     alt="">
    <br>
    Kringlecon 2 - CAPTEHA Solved!!
</div><br>

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image123.PNG"
     alt="">
    <br>
    Kringlecon 2 - You won!
</div><br>

After a few minutes you receive this email to notify you of your winning.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image125.PNG"
     alt="">
    <br>
    Kringlecon 2 - Winner notification.
</div><br>

#### Objective 8 - Solution
Answer:
```
8Ia8LiZEwvyZr2WO
```

---
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div><br>

## Objective 9 - Retrieve Scraps of Paper from Server

|    |       |
|----|-------|
|Inspirational Quote| "If you need answer, talk to a rubber duck!" -kaknowles |
|Objective|Gain access to the data on the Student Portal server and retrieve the paper scraps hosted there. What is the name of Santa's cutting-edge sleigh guidance system? For hints on achieving this objective, please visit the dorm and talk with Pepper Minstix.|
|Difficulty Level:|4|
|Links| [Student Portal](https://studentportal.elfu.org/)|  
|Related Video||

<br>
### Graylog - Terminal Challenge

|    |       |
|----|-------|
|Elf Name|Pepper Minstix|
|Pre-Solve Hints|[Graylog Docs](http://docs.graylog.org/en/3.1/pages/queries.html), (Events and Sysmon)|
|Post-Solve Hints| [Sqlmap Tamper Scripts](https://pen-testing.sans.org/blog/2017/10/13/sqlmap-tamper-scripts-for-the-win), [SQL Injection from OWASP](https://www.owasp.org/index.php/SQL_Injection) |
|Objective||

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image126.PNG"
     alt="">
    <br>
    Kringlecon 2 - Graylog - Terminal Challenge
</div><br>  

You read the Graylog Docs. You start the terminal challenge and login with credential ```elfustudent/elfustudent```. You use various search parameters to find the answers to the questions.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image127.PNG"
     alt="">
    <br>
    Kringlecon 2 - Graylog Incident Response Report - Terminal Challenge
</div><br>  



#### Graylog - Solution:
Answer:
```
ElfU Graylog Incident Response Report
Graylog Login:
elfustudent/elfustudent.

Question 1:
Minty CandyCane reported some weird activity on his computer after he clicked on a link in Firefox for a cookie recipe and downloaded a file.
What is the full-path + filename of the first malicious file downloaded by Minty?
Answer: C:\Users\minty\Downloads\cookie_recipe.exe
Hint: We can find this searching for sysmon file creation event id 2 with a process named firefox.exe and not junk .temp files. We can use regular expressions to include or exclude patterns:

TargetFilename:/.+\.pdf/

Question 2:
The malicious file downloaded and executed by Minty gave the attacker remote access to his machine. What was the ip:port the malicious file connected to first?
Answer: 192.168.247.175:4444
Hint: We can pivot off the answer to our first question using the binary path as our ProcessImage

Question 3:
What was the first command executed by the attacker? (answer is a single word)
Answer: C:\Windows\system32\cmd.exe /c "whoami "
Hint: Since all commands (sysmon event id 1) by the attacker are initially running through the cookie_recipe.exe binary, we can set its full-path as our ParentProcessImage to find child processes it creates sorting on timestamp.
Search: "ParentProcessCommandLine:/.*cookie_recipe.*/"

Question 4:
What is the one-word service name the attacker used to escalate privileges?
Answer: webexservice
Hint: Continuing on using the cookie_reciper.exe binary as our ParentProcessImage, we should see some more commands later on related to a service.

Question 5:
What is the file-path + filename of the binary ran by the attacker to dump credentials?
Answer: C:\cookie.exe
Hint: The attacker elevates privileges using the vulnerable webexservice to run a file called cookie_recipe2.exe. Let's use this binary path in our ParentProcessImage search.

Question 6:
The attacker pivoted to another workstation using credentials gained from Minty's computer. Which account name was used to pivot to another machine?
Answer: alabaster
Hint:Windows Event Id 4624 is generated when a user network logon occurs successfully. We can also filter on the attacker's IP using SourceNetworkAddress.
Search: EventID:4624 AND SourceNetworkAddress:192.168.247.175

Question 7:
What is the time ( HH:MM:SS ) the attacker makes a Remote Desktop connection to another machine?
Answer
Answer: 06:04:28
Hint: LogonType 10 is used for successful network connections using the RDP client.
Search: EventID:4624 AND SourceNetworkAddress:192.168.247.175

Question 8:
The attacker navigates the file system of a third host using their Remote Desktop Connection to the second host. What is the SourceHostName,DestinationHostname,LogonType of this connection? (submit in that order as csv)
Answer: ELFU-RES-WKS2,elfu-res-wks3,3
Search: ventID:4624 AND SourceHostName:ELFU\-RES\-WKS2
Hint:The attacker has GUI access to workstation 2 via RDP. They likely use this GUI connection to access the file system of of workstation 3 using explorer.exe via UNC file paths (which is why we don't see any cmd.exe or powershell.exe process creates). However, we still see the successful network authentication for this with event id 4624 and logon type 3.

Question 9:
What is the full-path + filename of the secret research document after being transferred from the third host to the second host?
Answer: C:\Users\alabaster\Desktop\super_secret_elfu_research.pdf
Hints:
Search EventID:2 AND source:elfu\-res\-wks2 AND NOT TargetFilename:/.+AppData.+/
We can look for sysmon file creation event id of 2 with a source of workstation 2. We can also use regex to filter out overly common file paths using something like:
AND NOT TargetFilename:/.+AppData.+/


Question 10:
What is the IPv4 address (as found in logs) the secret research document was exfiltrated to?
Answer: 104.22.3.84
Hint: We can look for the original document in CommandLine using regex.
When we do that, we see a long a long PowerShell command using Invoke-Webrequest to a remote URL of https://pastebin.com/post.php.
We can pivot off of this information to look for a sysmon network connection id of 3 with a source of elfu-res-wks2 and DestinationHostname of pastebin.com.
Search: pastebin.com

```
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image129.PNG"
     alt="">
    <br>
    Kringlecon 2 - Report Submission
</div><br>  


Message from Pepper Ministix after solving the challenge:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image128.PNG"
     alt="">
    <br>
    Kringlecon 2 - Graylog Incident Response Report - Terminal Challenge
</div><br>  


### Objective 9 - Walkthrough
You read the hints that were provided from solving the last terminal challenge. You look at the student portal.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image130.PNG"
     alt="">
    <br>
    Kringlecon 2 - Check Application Status
</div><br>  

You try a simple SQL injection ```'email@domain.com``` to ese if the website is vulnerable to SQL injection.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image131.PNG"
     alt="">
    <br>
    Kringlecon 2 - SQL injection
</div><br>  


After reviewing the webpage you notice that the CSRF validaitor url is ```https://studentportal.elfu.org/validator.php```

You download SQLMAP. You use the following configs:

```
url = https://studentportal.elfu.org/application-check.php?elfmail=test%40test.com&token=
method = get
csrfToken = token
csrfUrl = https://studentportal.elfu.org/validator.php
csrfMethod = GET
verbose = 6
```

You run SQLMAP with -dump. You get an error message that it's unable to find the CSRF token.

You search github to see where this error is coming from. You notice this error is coming from ```connect.py``` file around line 1110.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image137.PNG"
     alt="">
    <br>
    Kringlecon 2 - Interesting table
</div><br>  

You review the code and add 3 lines to "FIX" the code.

``` python
print ("page:" +str(page))
token.name="token"
token.value=str(page).replace("=","%3D")
```

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image136.PNG"
     alt="">
    <br>
    Kringlecon 2 - connect.py "FIX"
</div><br>  

You re-run SQLMAP with -dump.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image134.PNG"
     alt="">
    <br>
    Kringlecon 2 - SQLMAP Running.
</div><br>  

SQLMAP finds a database that has 6 image uids.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image135.PNG"
     alt="">
    <br>
    Kringlecon 2 - Interesting table
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image133.PNG"
     alt="">
    <br>
    Kringlecon 2 - SQLMAP completed.
</div><br>  

You download the 6 images that you found in the table.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\0f5f510e.png"
     alt="">
    <br>
    Kringlecon 2 - 0f5f510e.png
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\1cc7e121.png"
     alt="">
    <br>
    Kringlecon 2 - 1cc7e121.png
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\439f15e6.png"
     alt="">
    <br>
    Kringlecon 2 - 439f15e6.png
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\667d6896.png"
     alt="">
    <br>
    Kringlecon 2 - 667d6896.png
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\adb798ca.png"
     alt="">
    <br>
    Kringlecon 2 - adb798ca.png
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\ba417715.png"
     alt="">
    <br>
    Kringlecon 2 - ba417715.png
</div><br>  


You make out the name of Santa's cutting-edge sleigh guidance system on the edges of the scrapes.
<br>
#### Objective 9 - Solution
Answer:
```
Super sled-o-matic
```
---
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div><br>

## Objective 10 - Recover Cleartext Document

|    |       |
|----|-------|
|Inspirational Quote| "Solve objectives to unravel the mystery <strike>of the universe</strike>." - Ed Skoudis |
|Objective|The Elfscrow Crypto tool is a vital asset used at Elf University for encrypting SUPER SECRET documents. We can't send you the source, but we do have debug symbols that you can use. Recover the plaintext content for this encrypted document. We know that it was encrypted on December 6, 2019, between 7pm and 9pm UTC. What is the middle line on the cover page? (Hint: it's five words) For hints on achieving this objective, please visit the NetWars room and talk with Holly Evergreen.|
|Difficulty Level:| 5 |  
|Links|[Elfscrow Crypto](https://downloads.elfu.org/elfscrow.exe), [debug symbols](https://downloads.elfu.org/elfscrow.pdb), [encrypted document](https://downloads.elfu.org/ElfUResearchLabsSuperSledOMaticQuickStartGuideV1.2.pdf.enc)|  
|Related Video|[Ron Bowes, Reversing Crypto the Easy Way](https://www.youtube.com/watch?v=obJdpKDpFBA&list=PLjLd1hNA7YVzyhhqBQaW-tF45xnS6oHAP)|

<br>
###  Mongo Pilfer - Terminal Challenge

|    |       |
|----|-------|
|Elf Name|Holly Evergreen|
|Pre-Solve Hints|[MongoDB Documentation](https://docs.mongodb.com/manual/reference/command/listDatabases/#dbcmd.listDatabases)|
|Post-Solve Hints| [Reversing Crypto the Easy Way](https://youtu.be/obJdpKDpFBA)|
|Objective||

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image138.PNG"
     alt="">
    <br>
    Kringlecon 2 - Holy Evergreen - Terminal Challenge
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image139.PNG"
     alt="">
    <br>
    Kringlecon 2 - Mongo Pilfer - Terminal Challenge
</div><br>  

You read the hint provided by Holly Evergreen. You open the Mongo Pilfer terminal.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image140.PNG"
     alt="">
    <br>
    Kringlecon 2 - Mongo Pilfer - Terminal Challenge
</div><br>  


You run ```mongo``` and receive this error message.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image141.PNG"
     alt="">
    <br>
    Kringlecon 2 - Mongo Pilfer - Terminal Challenge
</div><br>  

You notice Mongo is not running on a default port.

You look around and find a file in the root ```go.sh```.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image142.PNG"
     alt="">
    <br>
    Kringlecon 2 - cat /go.sh
</div><br>  

This file shows that mongo is running on port 12121.

You run ```mongo localhost:12121``` to connect to the mongo server.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image143.PNG"
     alt="">
    <br>
    Kringlecon 2 - Mongo Pilfer - Terminal Challenge
</div><br>  

You run ```show dbs``` to get a list of databases. You switch to ```elfu``` database. You list the collections ```show collections```.

You run the action ```find``` on collection ```solution```.

You run the command that is displayed from the above command.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image144.PNG"
     alt="">
    <br>
    Kringlecon 2 - Mongo Pilfer - Terminal Challenge
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image145.PNG"
     alt="">
    <br>
    Kringlecon 2 - Mongo Pilfer - Terminal Challenge
</div><br>  


####  Mongo Pilfer - Solution:
Answer:
```
mongo localhost:12121
db.loadServerScripts();displaySolution();
```

Message from Holly Evergreen after solving the challenge:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image146.PNG"
     alt="">
    <br>
    Kringlecon 2 - Mongo Pilfer - Terminal Challenge
</div><br>  


### Objective 10 - Walkthrough
You watch the Reversing Crypto the Easy Way.

You run ```elfscrow.exe``` in a sandbox and encrypt a test document. You notice each time the document is encrypted it is providing a different escrow key.

You start by downloading and installing the free version of IDA. You download the symbols provided in the challenge. You open ```elfscrow.exe``` in IDA and load the symbols.

You navigate to ```generate_key``` function. You notice the function is calling the time. After the time function has been called it's calling the ```super_secure_srand``` function.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image147.PNG"
     alt="">
    <br>
    Kringlecon 2 - Ida Generate_key function
</div><br>  

You google the time function and notice that it returns the time in epoch.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image148.PNG"
     alt="">
    <br>
    Kringlecon 2 - time function
</div><br>  


You write a python program to output time in epoch.

``` Python
import time
i=1
while i < 100:
    seconds = int(time.time())
    print("Seed =", seconds)
    i += 1

```

You run ```elfscrow.exe``` at the same time as the python script and confirm that ```elfscrow.exe``` is using is time() as the Seed.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image165.PNG"
     alt="">
    <br>
    Kringlecon 2 - Elfscrow.exe
</div><br>  

From earlier, you know this seed is likely passed to ```super_secure_srand``` function.
You review ```super_secure_srand```.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image149.PNG"
     alt="">
    <br>
    Kringlecon 2 - super_secure_srand function
</div><br>  

You see a few constant in this function, ex. ```2531011```.

You search Google for this constant. You find a Fastrand() function that uses the same constants.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image150.PNG"
     alt="">
    <br>
    Kringlecon 2 - Fastrand()
</div><br>  

You remember the video talked about how to create a generate_key function.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image151.PNG"
     alt="">
    <br>
    Kringlecon 2 - Screenshot from the talk
</div><br>  
Using the video as a guide, you write the generate_key() function.

``` Python
def generate_key(seed):
    key=""
    for i in range(8):
        seed=(214013*seed + 2531011)
        key +=  chr(((seed >> 16)&0x7fff)&0x0ff)
    return key

```

While reviewing the code, you find that the encryption is likely DES-CBC.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image154.PNG"
     alt="">
    <br>
    Kringlecon 2 - DES-CBC key
</div><br>  

You test decrypting the file you encrypted on [CyberChef](https://gchq.github.io/CyberChef/).

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image155.PNG"
     alt="">
    <br>
    Kringlecon 2 - Decrypt the file encrypted by elfscrow.exe
</div><br>  

The objective states the file was encrypted on December 6, 2019, between 7pm and 9pm UTC. You convert the time to epoch time.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image159.PNG"
     alt="">
    <br>
    Kringlecon 2 - epoch time December 6, 2019, 7 PM

</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image160.PNG"
     alt="">
    <br>
    Kringlecon 2 - epoch time December 6, 2019, 9 PM
</div><br>

You know the key is between 1575658800 and 1575666000.
You write a For loop around generate_key() function to generate all the keys. You output all the keys to a ```keys.txt```.

You download [CyberChef API](https://github.com/gchq/CyberChef/wiki/Node-API) from github.

You write a wrapper in Javascript to open ```keys.txt``` and decrypt it using CyberChef framework. You use the DES-CBC to decrypt the ```ElfUResearchLabsSuperSledOMaticQuickStartGuideV1.2.pdf.enc``` with all possible keys. You output the decrypted files to a folder with the key that was used to decrypt it as the filename.

{% highlight JavaScript linenos %}
// app.js
const chef = require("cyberchef");
var readline = require('readline');
const fs = require('fs');


let file = fs.readFileSync("ElfUResearchLabsSuperSledOMaticQuickStartGuideV1.2.pdf.enc");
console.log(file) ;


var myInterface = readline.createInterface({
  input: fs.createReadStream('keys.txt')
});

var lineno = 0;
myInterface.on('line', function (line) {
  lineno++;
  console.log('Line number ' + lineno + ': ' + line.trim());

    try {
      var results = chef.DESDecrypt(file,{
                Key:{string:line.trim(), option:"Hex"},
                IV:{string:"0000000000000000", option:"Hex"},
                Mode: "CBC",
                Input:"Raw",
                Output:"Raw"},).toString();
      //  console.log(results);

      fs.writeFileSync('./files/'.concat(line.trim()), results, "binary",(err) => {
          // throws an error, you could also catch it here
          if (err) throw err;

          // success case, the file was saved
          console.log('Lyric saved!');
      });

      results = ''


            }
    catch(err) {
    }
});

{% endhighlight JavaScript %}

You run the JavaScript file and wait until it has decrypted the file with all possible keys.

Once completed, you run the command ```grep -rl "%PDF"``` to find the decrypted file that has a PDF header.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image161.PNG"
     alt="">
    <br>
    Kringlecon 2 - The only decrypted file with the "%PDF" header
</div><br>

The key used to encrypt the file is ```b5ad6a321240fbec```.

You open the decrypted file.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image163.PNG"
     alt="">
    <br>
    Kringlecon 2 - Document decrypted
</div><br>

You notice an interesting section in the file that may come handy later.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image166.PNG"
     alt="">
    <br>
    Kringlecon 2 - Document decrypted
</div><br>


#### Objective 10 - Solution
Answer:
```
Machine Learning Sleigh Route Finder
```
---
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div><br>

## Objective 11 - Open the Sleigh Shop Door

|    |       |
|----|-------|
|Inspirational Quote| "You must learn to say 'no'" -hacks4pancake  |
|Objective|Visit Shinny Upatree in the Student Union and help solve their problem. What is written on the paper you retrieve for Shinny? For hints on achieving this objective, please visit the Student Union and talk with Kent Tinseltooth.|
|Difficulty Level:|5|
|Links| [Crate](https://crate.elfu.org/)|  
|Related Video||
<br>

### Smart Braces - Terminal Challenge

|    |       |
|----|-------|
|Elf Name|Kent Tinseltooth|
|Pre-Solve Hints|[Iptables](https://upcloud.com/community/tutorials/configure-iptables-centos/)|
|Post-Solve Hints| [Chrome Dev Tools](https://developers.google.com/web/tools/chrome-devtools) |
|Objective||

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image167.PNG"
     alt="">
    <br>
    Kringlecon 2 - Kent Tinseltooth - Terminal Challenge
</div><br>  

You open the console and see the following messages:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image168.PNG"
     alt="">
    <br>
    Kringlecon 2 - Smart Braces - Terminal Challenge
</div><br>  

You read IOTteethBraces.md.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image169.PNG"
     alt="">
    <br>
    Kringlecon 2 - IOTteethBraces.md
</div><br>  

This is a timed challenge. If you take too long to solve the challenge, you're greeted with the following message:

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image170.PNG"
     alt="">
    <br>
    Kringlecon 2 - Kent Tinseltooth - Terminal Challenge
</div><br>  

You read the hint for this challenge and write the IP tables for the challenge.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image171.PNG"
     alt="">
    <br>
    Kringlecon 2 - Kent Tinseltooth - Terminal Challenge
</div><br>  


####  Smart Braces - Solution:
Answer:
```
sudo iptables -F
sudo iptables -P FORWARD DROP
sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT DROP
sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A OUTPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

sudo iptables -A INPUT -p tcp -s 172.19.0.255 --dport 22 -j ACCEPT
sudo iptables -A INPUT -p tcp --match multiport --dport 21,80 -j ACCEPT
sudo iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -i lo -j ACCEPT
```

Message from Kent Tinseltooth after solving the challenge:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image172.PNG"
     alt="">
    <br>
    Kringlecon 2 - Kent Tinseltooth - Terminal Challenge
</div><br>  


### Objective 11 - Walkthrough
You visit Shinny Upatree and are greeted with this message:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image173.PNG"
     alt="">
    <br>
    Kringlecon 2 - Shinny Upatree
</div><br>  

When you visit [crate](https://crate.elfu.org/) website, you're greeted with a number of locks that you have to open. Each lock provides hint(s) for opening the lock.
<br>
#### Lock 1

You open the chrome developer tools and see a code ```62ID5140```. You type this code in lock 1 and it unlocks.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image174.PNG"
     alt="">
    <br>
    Kringlecon 2 - Lock 1
</div><br>  

#### Lock 2
You proceed to lock 2.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image175.PNG"
     alt="">
    <br>
    Kringlecon 2 - Lock 2
</div><br>  

You view the source code for lock 2 and see the code ```5U7A9BBX```.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image177.PNG"
     alt="">
    <br>
    Kringlecon 2 - Lock 2 Source Code
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image176.PNG"
     alt="">
    <br>
    Kringlecon 2 - Lock 2 - Print Preview
</div><br>  

#### Lock 3
You proceed to lock 3.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image178.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 3
</div><br>  

You view the Network response in chrome developer tools.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image179.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 3 - Network response
</div><br>  

You load the ```.png``` file that you see in network response.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image180.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 3 - png
</div><br>  

You type the code in lock 3 to unlock it.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image181.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 3 - Solved
</div><br>  

#### Lock 4
You proceed to lock 4.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image182.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 4
</div><br>  

You go to ```Application``` tab in chrome developer tools and expand ```Local Stroage``` under ```Storage```.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image183.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 4 - Local Storage
</div><br>  

You type the code to unlock lock 4.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image184.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 4 - Solved
</div><br>  

#### Lock 5
You proceed to Lock 5.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image185.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 5
</div><br>  

The hint says to view the title on the html page. You view the title.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image186.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 5 - html
</div><br>  

You type the code in lock 5 to unlock it.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image187.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 5 - Solved
</div><br>  

#### Lock 6
You proceed to Lock 6.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image188.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 6
</div><br>  

You view the .css file and update the ```perspective``` variable.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image190.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 6 - .css
</div><br>  

The code becomes visible.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image191.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 6 - .css
</div><br>  

You type the code in the lock.
<br>
#### Lock 7
You proceed to Lock 7.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image192.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 7
</div><br>  

You view the ```font-family``` in the html file and see ```QCIAX2SW```
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image193.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 7 - font-family html
</div><br>  

You type the code to unlock lock 7.
<br>
#### Lock 8
You proceed to Lock 8
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image194.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 8
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image195.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 8 - Code analysiss
</div><br>  

You create a button ```.egg``` and get the event listener.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image197.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 8 - Event Listener
</div><br>  

You enter ```VERONICA``` into the lock to unlock it.
<br>
#### Lock 9
You proceed to lock 9.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image198.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 9
</div><br>  

You set the chakra's in the code to active. You see that the code appears above the instructions.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image199.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 9
</div><br>  

You type the code into the lock to unlock.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image200.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 9 - Solved
</div><br>  

#### Lock 10
You proceed to lock 10.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image201.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 10
</div><br>  

You view the code for the lock.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image202.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 10 - Code
</div><br>  


You remove the ```"cover"```.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image203.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 10 - Remove Cover
</div><br>  

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image204.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 10
</div><br>  

When you try to type a code the lock, an error appears in the console that it's missing a macaroni. You search the code for macaroni and find this.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image205.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 10 - macaroni
</div><br>  

You look at the .css and find that there is a mac.png, qtip.png and gnome.png.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image206.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 10 - png, qtip.png and gnome.png
</div><br>  

You look for gnome in the code.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image207.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 10 - gnome
</div><br>  

You find swab in the code.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image208.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 10 - swab/qtip
</div><br>

You copy the three components to the lock 10 code.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image209.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 10 - Fix circuit board
</div><br>

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image210.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 10 - Fixed lock
</div><br>

You zoom into the side of the circuit board to find the code to unlock the lock ```K029XJ37```.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image213.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 10 - code
</div><br>

You're greeted by this message once you unlock lock 10.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image214.PNG"  
     alt="">
    <br>
    Kringlecon 2 - Lock 10 - code
</div><br>


#### Objective 11 - Solution
Answer:
```
Lock 1: 62ID5140
Lock 2: 5U7A9BBX
Lock 3: FZUNIJFD
Lock 4: H0UHDN8S
Lock 5: ZW5698HD
Lock 6: SRB40Q5Q
Lock 7: QCIAX2SW
Lock 8: VERONICA
Lock 9: 0QIMRKYC
Lock 10: K029XJ37

The villian is The Tooth Fairy.
```

---
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div><br>

## Objective 12 - Filter Out Poisoned Sources of Weather Data

|    |       |
|----|-------|
|Inspirational Quote| "A Nerarious, villainous, Evil attacker is the worst of attacker you can have." -Ed Skoudis|
|Objective|Use the data supplied in the Zeek JSON logs to identify the IP addresses of attackers poisoning Santa's flight mapping software. Block the 100 offending sources of information to guide Santa's sleigh through the attack. Submit the Route ID ("RID") success value that you're given. For hints on achieving this objective, please visit the Sleigh Shop and talk with Wunorse Openslae.|
|Difficulty Level:|4|
|Links| [Zeek JSON logs](https://downloads.elfu.org/http.log.gz), [Block the 100 offending sources of information to guide Santa's sleigh](https://srf.elfu.org/)|  
|Related Video||

<br>
### Zeek JSON Analysis - Terminal Challenge

|    |       |
|----|-------|
|Elf Name|Wunorse Openslae|
|Pre-Solve Hints|[Parsing Zeek JSON Logs with JQ](https://pen-testing.sans.org/blog/2019/12/03/parsing-zeek-json-logs-with-jq-2)|
|Post-Solve Hints|Do you see any [LFI](https://www.owasp.org/index.php/Testing_for_Local_File_Inclusion), [XSS](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)), [Shellshock](https://en.wikipedia.org/wiki/Shellshock_(software_bug)), or [SQLi](https://www.owasp.org/index.php/SQL_Injection)?|
|Objective||

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image215.PNG"
     alt="">
    <br>
    Kringlecon 2 - Zeek JSON Analysis - Terminal Challenge
</div><br>  


You read the instructions for jq. You open the terminal console.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image216.PNG"
     alt="">
    <br>
    Kringlecon 2 - Zeek JSON Analysis - Terminal Challenge
</div><br>  

You use jq to find the longest durations.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image217.PNG"
     alt="">
    <br>
    Kringlecon 2 - Zeek JSON Analysis - Terminal Challenge
</div><br>  

You modify the query to display the host and destinations.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image218.PNG"
     alt="">
    <br>
    Kringlecon 2 - Zeek JSON Analysis - Terminal Challenge
</div><br>  

You modify the query to sort by duration and get the last item of the list.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image219.PNG"
     alt="">
    <br>
    Kringlecon 2 - Zeek JSON Analysis - Terminal Challenge
</div><br>  

You run the ```runtoanswer``` and type in ```13.107.21.200```.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image220.PNG"
     alt="">
    <br>
    Kringlecon 2 - Zeek JSON Analysis - Terminal Challenge
</div><br>  




####  Zeek JSON Analysis - Solution:
Answer:
```
13.107.21.200
```

Message from Wunorse Openslae after solving the challenge:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image222.PNG"
     alt="">
    <br>
    Kringlecon 2 - Wunorse Openslae - Terminal Challenge
</div><br>  

<br>
### Objective 12 - Walkthrough

You download zeek logs. We need to find the credentials to login to the website.

You use JQ to filter out the noise and view successful connections.

```
jq '.[] | select (.uri | contains ("weather?station") | not) | select (.status_code == 200) | .uri' http.log | sort |uniq
```

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image223.PNG"
     alt="">
    <br>
    Kringlecon 2 - Filter out the noise using JQ
</div><br>  

You see a file name ```README.md```. You remember the document you decrypted in an earlier challenge, referred to default credentials being stored in ```README.md```.

You access ```srf.elfu.org/README.md```.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image224.PNG"
     alt="">
    <br>
    Kringlecon 2 - README.md
</div><br>  

You login ```srf.elfu.org``` with the default login.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image225.PNG"
     alt="">
    <br>
    Kringlecon 2 - srf login page
</div><br>  

The welcome page once you login to ```srf```.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image226.PNG"
     alt="">
    <br>
    Kringlecon 2 - srf welcome page
</div><br>  

You review the Firewall instructions on how to block and allow IPs.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image227.PNG"
     alt="">
    <br>
    Kringlecon 2 - Firewall Instructions
</div><br>  

You use JQ and the hints to find some of the bad IPs:
```
jq -j '.[] |  .["id.orig_h"], ", ",.["user_agent"],", ", .uri, ", ",.username, ", ",.password, ", ",.host , "\n"' http.log | grep -E \' > blah.csv
jq -j '.[] |  .["id.orig_h"], ", ",.["user_agent"],", ", .uri, ", ",.username, ", ",.password, ", ",.host,  "\n"' http.log | awk  '/\/\.\./' >> blah.csv
jq -j '.[] |  .["id.orig_h"], ", ",.["user_agent"],", ", .uri, ", ",.username, ", ",.password, ", ",.host,  "\n"' http.log | grep -E "\.\." >> blah.csv
jq -j '.[] |  .["id.orig_h"], ", ",.["user_agent"],", ", .uri, ", ",.username, ", ",.password, ", ",.host,  "\n"' http.log | grep -E \/\.\% >> blah.csv
jq -j '.[] |  .["id.orig_h"], ", ",.["user_agent"],", ", .uri, ", ",.username, ", ",.password, ", ",.host,  "\n"' http.log | grep pass >> blah.csv
jq -j '.[] |  .["id.orig_h"], ", ",.["user_agent"],", ", .uri, ", ",.username, ", ",.password, ", ",.host,  "\n"' http.log | grep \> >> blah.csv
jq -j '.[] |  .["id.orig_h"], ", ",.["user_agent"],", ", .uri, ", ",.username, ", ",.password, ", ",.host,  "\n"' http.log | grep \& >> blah.csv
jq -j '.[] |  .["id.orig_h"], ", ",.["user_agent"],", ", .uri, ", ",.username, ", ",.password, ", ",.host,  "\n"' http.log | grep \| >> blah.csv
jq -j '.[] |  .["id.orig_h"], ", ",.["user_agent"],", ", .uri, ", ",.username, ", ",.password, ", ",.host,  "\n"' http.log | awk '/\;\s*\}/' >> blah.csv
```

From the above queries you get 78 Bad IPs. You know there is about 100 bad IPs. You export all the events to a .csv file.
```
jq -j '.[] |  .["id.orig_h"], ", ",.["user_agent"],", ", .uri, ", ",.username, ", ",.password, ", ",.host,  "\n"' http.log | > all.csv
```

You open ```all.csv``` in excel and look at the data.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image230.PNG"
     alt="">
    <br>
    Kringlecon 2 - Pivot table on the User-Agent
</div><br>  

You use vlookup to get the user-agent count for each of the IP's user-agents. You filter on user-agent count that are low.
You filter out the IPs that are already in your bad IP list.

<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image231.PNG"
     alt="">
    <br>
    Kringlecon 2 - Filter by user-agents that have low hits.
</div><br>  

You get about 39 new IPs.

```
103.235.93.133
118.26.57.38
44.164.136.41
249.237.77.152
203.68.29.5
10.122.158.57
187.152.203.243
50.154.111.0
217.132.156.225
252.122.243.212
29.0.183.220
22.34.153.164
66.116.147.181
126.102.12.53
31.116.232.143
250.22.86.40
140.60.154.239
226.102.56.13
42.127.244.30
104.179.109.113
42.103.246.130
42.103.246.130
42.103.246.130
42.103.246.130
185.19.7.133
42.16.149.112
158.171.84.209
34.155.174.167
249.90.116.138
231.179.108.238
92.213.148.0
97.220.93.190
87.195.80.126
53.160.218.44
253.65.40.39
226.240.188.154
148.146.134.52
142.128.135.10
37.216.249.50
```


You combine the bad IPs. Here is a list of bad IPs:

```
42.103.246.250,49.161.8.58,84.147.231.129,2.230.60.70,10.155.246.29,225.191.220.138,75.73.228.192,249.34.9.16,27.88.56.114,238.143.78.114,121.7.186.163,106.132.195.153,129.121.121.48,190.245.228.38,34.129.179.28,135.32.99.116,2.240.116.254,45.239.232.245,33.132.98.193,84.185.44.166,254.140.181.172,150.50.77.238,68.115.251.76,118.196.230.170,173.37.160.150,81.14.204.154,135.203.243.43,186.28.46.179,13.39.153.254,111.81.145.191,0.216.249.31,220.132.33.81,83.0.8.119,150.45.133.97,229.229.189.246,227.110.45.126,123.127.233.97,80.244.147.207,200.75.228.240,230.246.50.221,223.149.180.133,187.178.169.123,116.116.98.205,102.143.16.184,52.39.201.107,131.186.145.73,253.182.102.55,1.185.21.112,229.133.163.235,194.143.151.224,23.49.177.78,75.215.214.65,211.229.3.254,250.51.219.47,180.57.20.247,9.206.212.33,79.198.89.109,25.80.197.172,193.228.194.36,169.242.54.5,28.169.41.122,233.74.78.199,132.45.187.177,56.5.47.137,19.235.69.221,69.221.145.150,42.191.112.181,48.66.193.176,44.74.106.131,106.93.213.219,31.254.228.4,61.110.82.125,65.153.114.120,95.166.116.45,168.66.108.62,139.45.221.220,96.156.113.98,170.51.98.223,103.235.93.133,118.26.57.38,44.164.136.41,249.237.77.152,203.68.29.5,10.122.158.57,187.152.203.243,50.154.111.0,217.132.156.225,252.122.243.212,29.0.183.220,22.34.153.164,66.116.147.181,126.102.12.53,31.116.232.143,250.22.86.40,140.60.154.239,226.102.56.13,42.127.244.30,104.179.109.113,42.103.246.130,185.19.7.133,42.16.149.112,158.171.84.209,34.155.174.167,249.90.116.138,231.179.108.238,92.213.148.0,97.220.93.190,87.195.80.126,53.160.218.44,253.65.40.39,226.240.188.154,148.146.134.52,142.128.135.10,37.216.249.50
```

You block the IPs on the firewall.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image228.PNG"
     alt="">
    <br>
    Kringlecon 2 - Block bad IPs in firewall
</div><br>  
<br>
#### Objective 12 - Solution
Answer:
```
Route Calculation Success! RID:0807198508261964
```

Message from Tooth Fairy after solving the challenge:
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image229.PNG"
     alt="">
    <br>
    Kringlecon 2 - Tooth Fairy response
</div><br>  

<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div><br>

## Conclusion

Once you solve the challenge, the bell tower door opens up.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image230-1.PNG"
     alt="">
    <br>
    Kringlecon 2 - Bell Tower Access
</div><br>  

You go up the ladder to the bell tower.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image231-1.PNG"
     alt="">
    <br>
    Kringlecon 2 - Bell Tower Access
</div><br>  

You open the letter in the corner of the room.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image232.PNG"
     alt="">
    <br>
    Kringlecon 2 - Bell Tower
</div><br>  

You talk to Santa.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image233.PNG"
     alt="">
    <br>
    Kringlecon 2 - Santa
</div><br>  

You talk to Tooth Fairy.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image234.PNG"
     alt="">
    <br>
    Kringlecon 2 - Tooth Fairy
</div><br>  

You talk to Krampus.
<div style="text-align:center">
    <br>
     <img src="\assets\images\2020-01-10-KringleCon2\Image235.PNG"
     alt="">
    <br>
    Kringlecon 2 - Krampus
</div><br>  

The narrative of the story line:

```
Whose grounds these are, I think I know

His home is in the North Pole though

He will not mind me traipsing here

To watch his students learn and grow

Some other folk might stop and sneer

"Two turtle doves, this man did rear?"

I'll find the birds, come push or shove

Objectives given: I'll soon clear

Upon discov'ring each white dove,

The subject of much campus love,

I find the challenges are more

Than one can count on woolen glove.

Who wandered thus through closet door?

Ho ho, what's this? What strange boudoir!

Things here cannot be what they seem

That portal's more than clothing store.

Who enters contests by the ream

And lives in tunnels meant for steam?

This Krampus bloke seems rather strange

And yet I must now join his team...

Despite this fellow's funk and mange

My fate, I think, he's bound to change.

What is this contest all about?

His victory I shall arrange!

To arms, my friends! Do scream and shout!

Some villain targets Santa's route!

What scum - what filth would seek to end

Kris Kringle's journey while he's out?

Surprised, I am, but "shock" may tend

To overstate and condescend.

'Tis little more than plot reveal

That fairies often do extend

And yet, despite her jealous zeal,

My skills did win, my hacking heal!

No dental dealer can so keep

Our red-clad hero in ordeal!

This Christmas must now fall asleep,

But next year comes, and troubles creep.

And Jack Frost hasn't made a peep,

And Jack Frost hasn't made a peep...
```
