---
layout: post
title: Electron is it a cancer?
category: code
excerpt_separator:  <!--more-->
---

<img src="https://upload.wikimedia.org/wikipedia/commons/3/3f/Electron_0.36.4_Icon.png" alt="Electron" />

### Electron
Last week, there was a post by <a href="https://medium.com/@caspervonb/electron-is-cancer-b066108e6c32" target="_blank">Casper Beyer</a> arguing that, 'Electron is Cancer.' Now, I understand the reasoning for his argument, however, I feel that it is not a fair assessment. I will preface that I have never extended or built anything on top of an app on the Electron framework, but I would like to give my few cents.

I understand that it runs, predominately, in javascript through <a href="https://en.wikipedia.org/wiki/Node.js" target="_blank">Node.js</a>. This allows for a rather rapid development model for extending this framework for cross platform development. The author's argument that its performance is poor because it is not native, which is a solid case (he even did a benchmark on native apps verse electron based editors e.g. [atom and vs code]).

### Visual Studio Code
This IDE is amazing! On top of that it runs on my under-performing laptop that is more a brick than it is the former (you work with what you got)! Since I run in a Linux environment, naturally, Visual Studio Proper does not work, and I had been using a native IDE, <a href="https://en.wikipedia.org/wiki/MonoDevelop" target="_blank">MonoDevelop</a> for a number of years, but since .Net Core was released the functionality just has not been keeping up in features for which VS Code has been invested with. I will admit, it's been over a year since I have used it.

I had tried using <a href="https://en.wikipedia.org/wiki/JetBrains#Rider" target="_blank">Project Rider</a> an IDE that utilizes Resharper for the .Net environment. Maybe it was that I had tested it out in its early phases, but the performance was so bad that my poor little laptop could not even start up the IDE.

Is Visual Studio Code perfect? No, but something new is released every month, and to top it off my pc still handles it and there are always new extensions being developed for VS Code. The detriment of using native apps is that it must be compiled in each environment and using Node.js will be available in these other environments for you already.

### Are the suggested apps always better?
On a slight tangent, I have gone through numerous Desktop Environments that just never panned out. Oddly enough, I have been using <a href="https://en.wikipedia.org/wiki/MATE_(software)" target="_blank">Mate</a> (a fork of Gnome 2) on Ubuntu for a number of months now and so far that has been a really good setup. It has been argued that it is not the preferred environment for low resourced systems, but that will be a discussion for another day!

### Closing
Do I think Electron and its child projects is Cancer? No, I do not. It is just another tool to get the job done. If the market favours a more efficient environment then resources will be poured into it. Nothing lasts forever and something new will come along, eventually. Also, we can always work on improving the resource management of existing applications and frameworks. Simply put, if you like using other editors, feel free, and more power to you! I wrote this post with <a href="https://en.wikipedia.org/wiki/GNU_nano" target="_blank">Gnu nano</a>. ;)
