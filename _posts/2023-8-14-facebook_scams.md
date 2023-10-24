---
layout: post
title: Fighting Facebook Scammers
date: 2023-03-05 22:44 -0400
---
# **I hate Facebook.**   
Not so much the platform itself (although privacy is a serious concern), but mainly for the users it contains. Maybe it's cause I'm young, but seeing "REPOST IF YOU HAVE AMAZING GRANDKIDS" or "COPY AND PASTE THIS TO RESET THE MAGIC FACEBOOK ALGORITHM" hundreds of times per day just irks me for some reason. That being said, I love all the old grandmas and clueless moms in my rural hometown to death, and would be quite angry if someone tried to say, cheat them out of their Facebook credentials.  

Our story begins two years ago, when my mom received a DM asking if she was in a certain video, with a suspicious link. The link led to what appeared to be a Facebook login prompt, where she promptly presented her credentials. Soon after, she found that dozens of similar DMs were sent, asking others to click the link. We quickly reset her Facebook password and apologized to the users who were messaged. No harm, no foul.  

Fast forward to these last few weeks. I am getting notification after notification that one of my friends has tagged me in a post. This is an immediate red flag for me. I have friends? They are communicating with me? On Facebook? At the ripe old age of 19? Upon opening the notification, I see it's a phishing post, with a suspicious link captioned, "Just died in an accident" with a horrific car crash scene behind it.  

![an example of the horrible posts I saw.](/assets/img/fb_scams/example_post.png){:width="75%"}  

This upset me greatly - to play to the emotions of people who have lost loved ones in crashes is, to me, morally wrong and evil.  

So what do you do when you're pursuing a cybersecurity degree and you see evil online? You take down those no-good scammers! 

## **Becoming an Imposter**  

First, some reconnaissance. Let's open this link on my computer (in a VM of course, for security) so I can see it on the big screen!  

![without the proper user-agent, the link just redirects to WhatsApp.](/assets/img/fb_scams/no_user_agent.png){:width="75%"}  

Hold on a minute - when I clicked this on my phone, it took me to a phishing page, not WhatsApp!  

I think there's some trickery afoot, and it has to do with the "User-agent". Whenever you visit a website, your device, among other data, sends what's called a `User-agent` to the website. This contains data such as the version of your browser, whether it's a phone, tablet, or laptop, and other data about your browser. See what your user agent is [here](https://www.whatismybrowser.com/detect/what-is-my-user-agent/)! Ordinarily, this allows websites to serve you a more compact page if you're on a phone, or automatically give you the correct file depending on your operating system. In this case, the scammers have written some code to check if your user agent corresponds to being the Facebook in-app browser. If it's not, the link just redirects to a legit page. If the website detects you've fallen for the scam in the Facebook browser, it serves up the phishing page.  

So how can I pretend to be a Facebook in-app browser? I'll a [user-agent spoofing extension](https://chrome.google.com/webstore/detail/user-agent-switcher-for-c/djflhoibgkdhkhhcedjiklpkjnoahfmg) to add my own user-agent string that I found through using the Facebook browser.  

![success!](/assets/img/fb_scams/with_user_agent.png){:width="50%"}

Success! The scammer's site thinks we are the Facebook app!  

Here's the difference side-by-side, with and without the user-agent spoofer.

![comparison](/assets/img/fb_scams/contrast.png)

## **Reporting**  

With that out of the way, it's time to act. First, we need to find out who owns these websites. This is accomplished via a DNS WHOIS lookup. Every domain name, like [caydenwright.com](https://caydenwright.com), belongs to somebody. In my case, I purchased my domain from [Google Domains](https://domains.google.com). If you would perform a WHOIS on my website, you would see that it is owned by Google. This lookup can show you who to contact if you want to buy the domain, or in this case, tell the registrar that someone is abusing a domain. It is worth noting that many registrars do not publish their customer's real email, but rather publish a "proxy email" that goes to the registrant, but without exposing their true email.  

You can use [this](https://lookup.icann.org/en) website to perform a WHOIS on all your favorite sites!  

![A result of a WHOIS lookup on one of these malicious domains](/assets/img/fb_scams/whois.png){:width="60%"}

We've found who to contact to report this scam! We can see that they are protecting their name and email to avoid direct contact... While I could directly email them through the "proxy email" provided, I think that I'm going to report them to the registrar. As we can see, I need to email abuse@namecheap.com to report this domain.  

I've sent 5 emails today to several different hosting providers and registrars to get these phishing sites taken offline, and they kinda look like this.  

![an example email I sent to registrars to take down malicious sites](/assets/img/fb_scams/email.png)  

Hopefully they can respond quickly to protect innocent users.  

## **Have you fallen for such a phishing link?**  
Don't be so hard on yourself - it happens to even the best. Here are some steps you should take to secure your digital life:
1. Change your password.
    - IMMEDIATELY change your password to something secure, and hard to guess.
    - The longer you wait, the higer the risk of the attackers changing your password and locking you out of your account forever. 
    - Use a password manager!
2. Take down the post.
    - The less people that see the phishing link, the better (for your reputation, and for the potential victims.)
3. Take a closer look before you click.
    - Before you click, look at the link. Does it look like a website you've seen before? 
    - Before you type your password, is this a legit Facebook site? When in doubt, X it out.
<br><br>  

Now, why would someone want grandma's Facebook credentials? So what, they can make funny posts as grandma? While this is true, because the link is spread as accounts are compromised, there is more likely than not a more sinister purpose afoot. While I cannot confirm these theories, I have two ideas as to why these criminals are phishing for Facebook credentials.
1. \$$$
    - These criminals could be simply selling these credentials on the dark web for someone else to buy and use for their own purposes. 
    - Those other purposes could be any one of the following, or something entirely different.
2. Password re-use attack
    - If you use the same password for Facebook as you do your banking app, you're doing it wrong.
    - If you were to re-use the same password, and fall for the simple Facebook phishing attempt, an attacker could use your credentials on your banking portal, your iCloud account, your Instagram, or any of your other accounts.
3. Misinformation
    - An attacker with enough compromised Facebook accounts essentially has an army of voices to spread whatever lies they deem fit.
    - Imagine if all your friends started telling you to try a new product, or vote for a certain candidate, or visit a certain place - it would be pretty convincing, right?
    - With enough accounts, an attacker can make anything appear to be the truth.  

And that is my short and sweet tale of how I'm fighting a few phishing attempts.  
    
Inevitably, more will pop up, and my work will be overshadowed, but for now I feel pretty good about myself. Stay safe out there!