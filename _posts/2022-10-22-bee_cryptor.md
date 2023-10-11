---
layout: post
title: Bee-Cryptor
date: 2022-10-22 22:44 -0400
---
# Bee-Cryptor
It's been a while since my last post - I've been extremely busy since last year. I had a decent volleyball season, a great summer at camp, and now I'm attending the Rochester Institute of Technology for my Master's Degree in Computing Security! (turns out there's a lot of physics involved in Computer Engineering, and cybersecurity is cooler anyway). But this post isn't really about college - it's about a new piece of software I've written, and its inspiration comes from an old high school classmate.  

It was the spring of my junior year when I was taking Mrs. Wheland's PLTW Computer Science Principles. It was a rather small class, with just a handful of kids. Among those classmates was one of my greatest friends, Mason Diehl. Mason kept the class interesting: his quips and pranks and  "Mason-isms" kept the class laughing day after day. We needed to complete a final project for this class - and I was fresh out of ideas. Mason, in all of his infinite wisdom, tells me I should  "make something that encrypts text using the bee movie script".  

Ladies and Gentlemen, the [Bee-Cryptor](https://github.com/CWright2022/bee_cryptor).  

While the original Bee-Cryptor source code is lost to history (probably still on the file server at SCSD), that's probably a good thing. The original Bee-Cryptor could only handle lowercase letters, relied on humans to validate the  "wordlist", and in general had a lot of issues.  
But now, after a half-semester of Software Development and Problem Solving I, the Bee-Cryptor is back and better than ever! The Bee-Cryptor can take an input text, from a file or the command line, and  "encrypt" it using a  "wordlist".  

Essentially what the code does is take each character in your input, and convert it to a number (essentially uses Unicode encoding, but with an offset to make the wordlist requirements smaller). Then it takes that number, and returns a word from script.txt (the "wordlist").  
This can be anything (use the"-wordlist" option to change it), but it adds extra comedic value if you use the Bee Movie script. Bee-Cryptor will intelligently remove duplicate words from your wordlist in processing, so no need to worry about what you use for the wordlist.  
You can also input from a file! Just use the  "-encrypt_file" option at the prompt, then give a file name. This is useful if you need to encrypt something with a line feed in it - pasting to a terminal would not work properly.  
Bee-Cryptor will also put your encrypted text into a file named "output.txt" in the same directory as bee_cryptor.py. Keep in mind that this file is overwritten every time an encryption operation is performed.  

A few more things I want to add to Bee-Cryptor:  
1. Website demo - let people encrypt stuff online 
    - DONE! See my post about Bee-Cryptor Web!
2. API?
3. Expand character set (handle LF and CRLF)
4. Intelligent minimum wordlist length (base wordlist min length on characters in message)  

A few known limitations/bugs:  
1. Only supports Unicode characters space (decimal 32) through tilda (decimal 126).
    - could be expanded, but then wordlist would need to be bigger (intelligent minimum wordlist length could help)

I hope you'll "bee" the first to employ this new encryption standard that has everyone "buzzing"!

[Github link](https://github.com/CWright2022/bee_cryptor)