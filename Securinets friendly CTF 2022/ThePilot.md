
# Securinets Friendly CTF 2022 Writeup for THE PILOT forensics task

The Pilot

![](https://cdn-images-1.medium.com/max/2000/1*jYMYsSqWhvGNR4vYYz8aZg.png)

This is a forensics task given as a memory dump and our goal is to figure out the hidden information that will be our main flag .

To achieve this goal and get our flag we are going to use a tool called ***Volatility ***implemented to extract artifacts from the volatile memory samples

So to start we have to figure out the Profile name of this dump

![imageinfo is used to figure out the profile based on KDBG search](https://cdn-images-1.medium.com/max/2000/1*-XTk8kJabz2eXYC8LXxYNg.png)*imageinfo is used to figure out the profile based on KDBG search*

So the result of this command shows that the profile name is ***WinXPS2x86***

and by finding the profile we solve already the first subflag which was about determining the most appropriate volatility profile for this machine

![Subflag 2](https://cdn-images-1.medium.com/max/2000/1*BaaEGyhTBHXch3lVST7SXw.png)*Subflag 2*

To answer this question we can just pass our .dmp file throug md5sum and we figure out the hash of this dump that will be ***9200b1d9e8804ca472695e1b66a7925f***

![Subflag 3](https://cdn-images-1.medium.com/max/2000/1*5ijywgnoqLswvZcJU-Gn4w.png)*Subflag 3*

To get the hostname we have just to see the environment variables for each process using the envars command

![](https://cdn-images-1.medium.com/max/2000/1*HfKkBnVB9qW1eEi03w2CEw.png)

So as we see the computer name is ***UNKNOWN_F549DD2*** and that is our subflag

![Subflag 4](https://cdn-images-1.medium.com/max/2000/1*LXKRrt-9mcNLco-tMMYudA.png)*Subflag 4*

here we can just use the pslist command and we get our answer

![](https://cdn-images-1.medium.com/max/2000/1*ijQnDSE7m6joOExHMeQ7VA.png)

The PID is*** 584 ***and that is our subflag

![Subflag 5](https://cdn-images-1.medium.com/max/2000/1*E556Uce7OJDuq7UHsc6Wqw.png)*Subflag 5*

![](https://cdn-images-1.medium.com/max/2000/1*pSr1UV00txPpgKaEa-l3Zg.png)

The PID of the explorer is ***1308***

![Subflag 6](https://cdn-images-1.medium.com/max/2000/1*sOjKjesoRLYGJjkp8aeYgA.png)*Subflag 6*

from the 2 previous questions we find that the parent process of notepad.exe is 1308 which is the PID of the explorer and the date of start is so 2022–08–31 15:04:15

![Subflag 7](https://cdn-images-1.medium.com/max/2000/1*HKtrpd9SbGZsgI1mWffaGQ.png)*Subflag 7*

To scan the network of the machine we can use the command connscan

![](https://cdn-images-1.medium.com/max/2000/1*Ec9Mvb5v47mQ8hY_LwfNbQ.png)

the IP address is so ***192.168.1.130***

![Subflag 8](https://cdn-images-1.medium.com/max/2000/1*u4nbAfkSXn_4yupVWX8kkA.png)*Subflag 8*

To get this path we should display the process command line arguments using the command cmdline

![](https://cdn-images-1.medium.com/max/2000/1*Geah_LG3RyxiUJ_IV17hgA.png)

so our subflag is ***C:\WINDOWS\system32\ctfmon.exe***

![Subflag 9](https://cdn-images-1.medium.com/max/2000/1*4ZWhuMfRHbd4pECqSONO5w.png)*Subflag 9*

To get the CMD content we can use the command consoles and we got this output

![](https://cdn-images-1.medium.com/max/2000/1*xYY7UxOnLlR4qN7ReBR3UQ.png)

we put the output on cyberchef and we get our subflag

![](https://cdn-images-1.medium.com/max/2000/1*6gRn5JVoOTj584vSLUY9-A.png)

Securinets{TH3_BL4CK_LVguAge_15_AW350me}

![Subflag 10](https://cdn-images-1.medium.com/max/2000/1*qAcn-yG3bolLUrg29DNG3Q.png)*Subflag 10*

we use again the envars command

![](https://cdn-images-1.medium.com/max/2000/1*wuW4ZGniqly381NkKqSA8A.png)

and there is our subflag

![Subflag 11](https://cdn-images-1.medium.com/max/2000/1*6KL1B3CSQcw9ebOJmtLLrQ.png)*Subflag 11*

we can just make a filescan and we grep on Desktop

![](https://cdn-images-1.medium.com/max/2274/1*7Nf61RKpr4khhaRi27GvDQ.png)

now we just have to dump that file flag.png using the offset and we got our subflag in a png file

![](https://cdn-images-1.medium.com/max/2000/1*klViX-rTvcxD6yfnGjulng.png)

![Subflag 12](https://cdn-images-1.medium.com/max/2000/1*BKEL92j9svAROL7xC8U6ng.png)*Subflag 12*

Here we just have to use the clipboard command and we get our subflag

![](https://cdn-images-1.medium.com/max/2000/1*zeqn7uLFnOajcGIwbo59Cw.png)

![Subflag 13](https://cdn-images-1.medium.com/max/2000/1*MYixLp2v6qhLVwcUMTEIig.png)*Subflag 13*

to find this flag why not we try to pass our file to the strings command maybe it be helpful and lets grep on Securinets because we know that part of the flag

![](https://cdn-images-1.medium.com/max/2000/1*cJTVwMggAPvc-I5acFugVQ.png)

great we find already our subflag

Now let’s just move to the main flag

The main goal of this task is just to get out the information hidden inside the history of the browser

from the process list we can see that the browser in use is the explorer so let’s use the iehistory to figure out the history of this browser

![](https://cdn-images-1.medium.com/max/2000/1*QH8gxgKDiTdZgowOTqbNew.png)

as we see our user is using pastebin so let’s open that link maybe it is helpfull

![](https://cdn-images-1.medium.com/max/2000/1*KdM329m5yefHhp5YlfUPZA.png)

we just put it in cyberchef and there we will get our main flag

***Securinets{1_L0v3_CurL_FucK_Br0w5eRs}*** and here is our main flag
