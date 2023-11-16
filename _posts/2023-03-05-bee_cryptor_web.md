---
layout: post
title: Bee-Cryptor Web
date: 2023-03-05 22:44 -0400
---

# The Bee-Cryptor is now online!
Encrypt and decrypt to your heart's content without ever downloading a single .py file! [Click here to start encrypting!](https://bee-cryptor-web.vercel.app/) (It is now hosted on Vercel rather than RITSEC's OpenStack)  
This web app continues my series of silly Flask apps, after my IoT Thermal Printing project was a huge success. Essentially this is just a Flask app that uses the Bee-Cryptor as it's backend. Nothing fancy.  

What is interesting, however, is the way this is hosted. Being a member of RIT's security club, RITSEC, I have access to free cloud computing resources through our OpenStack instance. I finally learned how to properly spool up a Linux box, and decided to try hosting something on it. The only problem is public access - by default, I am not permitted to have a public IP. While I can simply ask the admin for one, I decided to take the challenge of hosting a web app with no public IP.  

I came across [Portmap](https://portmap.io/), which, through a VPN tunnel installed on the host (in this case my OpenStack VM), will give you a public DNS name and (random) port that links to the port you specified when you created the rule. I'm not sure of any better ways to do this, but it seems to work well for my little project. I'm really looking forward to using OpenStack more in the future! I have a lot of resources available to me through RITSEC to learn and grow my skillset.  

Update as of 11/16/23: The Bee-Cryptor is now hosted using [Vercel](https://vercel.com)! I made this change due to the troubles of uptime and remote access that came with using OpenStack - While I'm still very appreciative of RITSEC's resources, I found Vercel to better suit my needs.  

## Future Additions/Improvements: 
1. Performance enchancements
    - generate wordlist once rather than on every encryption
2. Better UI
    - add some pictures of bees
3. Allow custom wordlists
4. Instant encryption
    -display output as user is typing

[Source Code](https://github.com/CWright2022/bee_cryptor_web)