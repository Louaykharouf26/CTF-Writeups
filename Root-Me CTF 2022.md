
# Root-Me CTF 2022 Misc Challenges

This is my writeups for the misc challengs of root-me ctf

## Cheshire Cat

![Task Description](https://cdn-images-1.medium.com/max/2000/1*Vr6JCNdHqXrfCgUGNENQrg.png)*Task Description*

As the description tells this task is about to interact with a custom discord bot created by root-me admins

When we talk with the bot in the root-me discord server it tells us

![!help result](https://cdn-images-1.medium.com/max/2000/1*PT4oKFM61UUkS86R-4igdg.png)*!help result*

so let’s try !password and see what it gives

![!password](https://cdn-images-1.medium.com/max/2000/1*G5JZHQBTnBcWqUjyO3bEwA.png)*!password*

the bot says that he not answer just his master who will be the admin of the server

let’s now try to talk to DM the bot and see if this will help us to figure out the flag

![](https://cdn-images-1.medium.com/max/2000/1*Zyf5rVeVfvE5eEAU16wwKg.png)

the bot not like the DM and he asks for an invitation to the cup of tea

now it is a bit clear and it is all about finding a way to talk with this bot with an admin role

one of the ways is to invite “Cheshire” to a personal server where i m the owner let’s try this way by creating a server that i called taskctf and we try to invite the bot

first thing to do is to find the URL of any public bot available on discord

after that we change the URL of this public bot to make it suitable for Cheshire by getting the ID of Cheshire and changing the permission to 8 to give the bot full control also we change the scope to bot

the URL for our bot is now looking like this

![Cheshire invitation URL](https://cdn-images-1.medium.com/max/2000/1*dwZEON6hAMU5LVyc-yvE1w.png)*Cheshire invitation URL*

I just need now to invite the bot in my personal server and talk to him

![Personal server](https://cdn-images-1.medium.com/max/2096/1*nNitJFGYTkKg338ZVURtXg.png)*Personal server*

As we see here Cheshire talk to me as master and give me the password which will be the flag for this task ***RM{d0n’t_l3t_y0uR_b0Ts_pUbl1c}***

## The White Rabbit

![Task Description](https://cdn-images-1.medium.com/max/2000/1*iHOkLRv81tGNWj8EuXN37w.png)*Task Description*

This second task is also about interacting with a discord bot

first thing to do was to understand the commands of our bot

![bot commands](https://cdn-images-1.medium.com/max/2000/1*DvqH8k3hpyqIWonqlZF1Ag.png)*bot commands*

![ping role](https://cdn-images-1.medium.com/max/2000/1*lFJc8rt0-xiv3dkO2FgrMw.png)*ping role*

as it is clear here the bot is used to tells the situation of each challenge if it is up or down

Our role now is to find a way to exploit this to figure out the flag of this task

let’s try more the ping command

![](https://cdn-images-1.medium.com/max/2000/1*-WXf7i9rBcEEHihK88n1oA.png)

the result of the ping command is to write the argument in the challenge***.root-me.org

lets try to inject a command as an argument for the ping and see what happens

![](https://cdn-images-1.medium.com/max/2000/1*3VBPRwb-oBxlV5C4v3TW7A.png)

as it is clear the bot reject the first space bar that he find let’s try to put the command between “*** ; command;***” to bypass the space bar restriction and see the result

![](https://cdn-images-1.medium.com/max/2000/1*w7WG2jpyzkImXury9y5ewA.png)

so the ls command gives us the files that contains our bot lets try to read the flag.txt file

![](https://cdn-images-1.medium.com/max/2000/1*FVcJ_Yd8Ui9ga4rayiYGfA.png)

as it is clear the bot gives us the contents of flag.txt and that will be the flag of this task “***RM{D1sc0rD_t0_c0mm4nd_1nj3cTi0n}***”

## Applicatives Are The Way

![Task Description](https://cdn-images-1.medium.com/max/2000/1*bkzxD4q1c34ae_HzCHQLmw.png)*Task Description*

this task is given for us as a pcap file so it is about to analyse a network capture

![](https://cdn-images-1.medium.com/max/2330/1*tfPp4BlsQvsgFLjUMZ-qRA.png)

after a simple look on our pcap file we see that the packets were based on the TCP / FTP / ICMP / DNS

lets analyse the packets based on each protocol

we start with the TCP

once we follow the TCP we can see that the packet number 5 contains some codes that can be used to the ssl encryption for the packets this might be helpfull for the decryption

![](https://cdn-images-1.medium.com/max/2000/1*AR0kZiLDSU7Gmbw9etQiFA.png)

the first step is so to extract this keys on a log file.

after that we inject our log file on the preferences of wireshark and from that moment it will be used for the decryption of packets

![Wireshark configuration](https://cdn-images-1.medium.com/max/2000/1*wQhSr9miC6h5SX0tVBKxJw.png)*Wireshark configuration*

lets now follow the TLS stream for our packets and see what is happening there

![](https://cdn-images-1.medium.com/max/2000/1*xzVyPB8KUb8g9usGC0sihw.png)

it is now clear that the user was trying to get a zip file let’s see the TLS stream

![](https://cdn-images-1.medium.com/max/2000/1*V9XmxH3xJWu8wAvi1pEWQw.png)

the TLS stream shows that this zip contains a flag.txt file let’s save this flag.zip as a raw

once we save that zip file we can extract it is content by using foremost command

![](https://cdn-images-1.medium.com/max/2000/1*X6dUj0VZay39B1cfFvr2Tw.png)

so now we have the flag.txt file

![](https://cdn-images-1.medium.com/max/2000/1*hnTlpoeanMklPz8e9bSLMg.png)

to extract the flag.txt we need a password

once we follow the UDP stream we can find some parts of a code encoded with base64 and it tells us that the user lost his password

when i tried john to crack the password with the wordlist rockyou it doesn’t help me so we should see more inside our pcap file

we see that the user is sending some ping requests to the destination the ICMP packets contains some data lets think to get the data hidden in that packets and use them as a wordlist

![](https://cdn-images-1.medium.com/max/2000/1*fEP0UoFG7-3XRUaEJPHyeA.png)

now we have our wordlist let’s use it through john command and see if this will give us our flag

we make a hash file using zip2john and then we try to crack the password with john

![](https://cdn-images-1.medium.com/max/2000/1*JczansLjonsK0r6sLQcjmg.png)

so the password to extract flag.txt is **VKQ*{8cD]ZpfZn**

![](https://cdn-images-1.medium.com/max/2000/1*VFcySzElyYIuICWvZlna2g.png)

and here we get our flag : ***RM{W1r3Sh4rk_R3@lly_Is_Y0uR_Th1ng:)}***
