---
layout: post
title: The Message-Send-Inator
date: 2023-02-08 22:44 -0400
---

# Behold, Perry the Platypus, my Message-Send-Inator!

Recently for Christmas, I got one of these [little thermal printers](https://www.adafruit.com/product/597).  

Probably a weird thing to ask for, but I'm sure it's not the weirdest thing that I've ever asked for. 
![a picture of the thermal printer I got.](/assets/img/thermal_printer/printer.jpg)  

My initial idea was to make a "planner" of sorts, where the device prints out your schedule, the weather, and more every morning. While that project is also in the works, I decided to take a little detour to make a little gag project for me and my friends. 
![A photo of my janky device sitting in my dorm, awaiting a message](/assets/img/thermal_printer/thermal_printer.jpg){:width="50%"}  
My first adventure was to learn a little bit of web development. While I can certainly churn out a simple HTML document relatively easily, the backend is something I'm certainly unexperienced in. But since taking Software Dev 1 last semester, I know one thing pretty well, and that's Python. I had the printer already working with a basic [Python library from Adafruit](https://github.com/adafruit/Adafruit-Thermal-Printer-Library), so why not keep on the Python train? Enter [Flask](https://flask.palletsprojects.com/en/3.0.x/).  

I had only barely heard of flask before taking on this project - some guy from Computer Science House mentioned it to me when I was a member (for a whole week). I never really thought I would be using it much, that is, until I needed a web app written in Python. To those wondering, "Why would you write a web app in Python?", I present the following points.  
1. It's easy.
    - Python is easy to learn, and I can get quality code without jumping through a ton of hoops
2. This is a hobby project - it need not meet production-level speed and functionality. 
    - It will probably be cannibalized in a month or two to re-use the Pi for another project
3. Anything is better than PHP.  

![A few messages I got](/assets/img/thermal_printer/thermal_messages.jpg){:width="50%"}  

So now on to implementation. How did I do it? What's the secret sauce? Well lucky for you, [it's open source](https://github.com/CWright2022/iot_thermal_printer). Documentation exists in the GitHub repo as well, although I cannot guarantee full accuracy. A little "Google-fu" and knowledge of Python/Flask may be needed to run this for yourself.  

Fun fact: because the printer requires a decent bit of current at around 9V DC, I've had to MacGyver my Baofeng radio battery to power the printer. College is fun people!  

At the core of the app is app.py. This file contains the main app to be run by Gunicorn, the software that actually serves this app to the user. Within `app.py`, you'll see a flag like `@app.route('/', methods=["GET","POST"])`. This indicates to Flask/Gunicorn to run this function when we get a  HTTP GET or POST request to the root directory of the domain (was messagecayden.rit.edu - shoutout to RIT for owning a class B so I can just directly connect a bunch of stuff!)  

Within the function `name()`, you'll see "the magic" actually happen. First, we check to ensure that there haven't been more than 12 messages this hour. This is kept track of in a file called `./hourly_count.txt` so it can persist a reboot. If there is too many, then we generate the "too many" page `(./templates/too_many.html)`.  

If not, then we check for a POST request containing message data. We'll parse the data, print the message, increment both the hourly count and the all time count, then redirect the user with the flask redirect() function, returning HTTP 302 and directing the user to a dynamically generated success page. **This is important!** Without a redirect here, any refreshing of the browser would re-submit the form, leading to double printing of messages.  

That's basically it! Aside from the small amount of hate mail I got (getting hate mail from a receipt printer was not on my 2023 bucket list), this has been a really fun project! I enjoy seeing friends old and new send me all sorts of silly stuff to be printed right beside my bed!