---
layout: post
title: Open Office may expose your password to other users
---

Many of us, and especially system administrators, have tons of account passwords to remember. Strong password policies make remembering passwords a even more daunting task. Thus, the practice of storing these passwords in a password-protected file/registry which may be used to keep track of password changes, and in some cases, allow other administrators to take note of the credentials to other services/servers.

## How does this work?
For open office users, this could lead to the leakage of passwords to unauthorized users. This issue arises from the 'autocomplete' function that comes enabled with open office. How the autocomplete function works is that it will scan any document open for unique words based on a criteria, and store them in a list (which can be easily accessed through the options menu). However, what is troubling is that the default setting allows this list of words to be used after the document is closed. Therefore, opening a document containing your passwords may lead to the subsequent user being able to retrieve your passwords.

## Password protect it?
How this is different from the technique of browsing through recent documents is that this will work even if the original password file is saved with a password, encrypted or deleted from the computer. Fortunately though, the list disappears upon restarting the computer or by manually closing the process through the task manager.

## Recommendations
To protect against this specific problem in Open Office, it is highly recommended to check the option "When closing a document, remove the words collected from it from the list". This will prevent the above from recurring.

## Let's see it
Here's a quick demo on the issue mentioned.

{% include youtubePlayer.html id="0n6G3sEiax8" %}

> **Note: The information in this article is updated as of 12/12/2011.**
> 
> Also, thanks to Rodney [ rod.tan.90{at)gmail[d0t]com ]who helped with investigating the issue and taking the video!

