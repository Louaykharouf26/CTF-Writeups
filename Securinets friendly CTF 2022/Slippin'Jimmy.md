
# Securinets Friendly CTF 2022 First Writeup

Slippin’ Jimmy

Forensics Task ( Malware Analysis)

![](https://cdn-images-1.medium.com/max/2000/1*5dYHwmlV9pDGsRqNgUSI5A.png)

This challenge is given as a pcap file and it have as goal to find the IP address that this malware is communicating with

To analyse the packets captured in this pcap file we use the wireshark tool

![](https://cdn-images-1.medium.com/max/2730/1*Ec9wzbJLNfGSkQT10i_GVw.png)

As we see the packets are based on HTTP protocol and TCP protocol so we can just follow the TCP stream and the HTTP stream to have an idea of what is really happening inside each packet .

So we can now start finding each subflag till we end with the main flag of this task

![first subflag](https://cdn-images-1.medium.com/max/2000/1*x6ctJow-8NhWRUo3v8cHAA.png)*first subflag*

Once the file is opened in wireshark and using the first column of the results of the capture “time” column we can see that this operation took ***58*** seconds which the content of the time column of the last packet

![Second Subflag](https://cdn-images-1.medium.com/max/2000/1*gQmH0OJkN6NYFw58sAwfyg.png)*Second Subflag*

The victim’s Ip address is just the source of the first packet captured which is ***192.168.182.132***

![Subflag 3](https://cdn-images-1.medium.com/max/2000/1*u0bRceOix1Rm42kNA9mdLw.png)*Subflag 3*

To get the answer for this question we just need to follow the HTTP/TCP stream which will give us some informations of the content of the packet as the screenshot shows

![](https://cdn-images-1.medium.com/max/2000/1*ZeXjdC8fk69QEXUcOUAw2g.png)

here we see that the user-agent is ***Windows NT 5.1*** which is ***Windows XP*** and here you have the answer for this subflag

![Subflag 4](https://cdn-images-1.medium.com/max/2000/1*YPUcGKl8tZDTWrmkB_C6Ig.png)*Subflag 4*

Same as the third subflag to get the link of the webserver we have just to follow the HTTP/TCP stream and we will find out the host which will be : ***b68d-102–159–93–234.eu.ngrok.io***

![Subflag 5](https://cdn-images-1.medium.com/max/2000/1*zlLgyAqeKqr9MZl1-tdD_A.png)*Subflag 5*

This software is also obtained from the HTTP stream follow

![](https://cdn-images-1.medium.com/max/2000/1*sdIOVaH-kTAqBHtIAZbQHg.png)

so the server that hosts the phishing page is ***SimpleHTTP/0.6 Python/3.8.10*** and that is the subflag that we are looking for .

![Subflag 6](https://cdn-images-1.medium.com/max/2000/1*l9CxURviaqNaBeCQ63epUg.png)*Subflag 6*

When we investigate the packets of this capture we can see that there is a try to get the credentials of the user which can be found on the login.php file by a simple export of the file from wireshark

![](https://cdn-images-1.medium.com/max/2000/1*a8_gXFqEn6Dg4w7EikE33Q.png)

the content of the login.php is what we are looking for and by using the url-encode we got the right mail and password which is ***jamesmcgill@aol.com:Worlds2ndBe$tLawy3r***

![Subflag 7](https://cdn-images-1.medium.com/max/2000/1*8xQ7D1OxdglwW2h5sKRHOQ.png)*Subflag 7*

Here we can start using “Virus Total” which will be helpfull for the rest of the subflags

**Virus Total **is just a service used to detect the malwares and the virus that can a file contain

from the exported files we can export the statement.exe which will contain the malware and we start our analyse using virus total and we get this result :

![](https://cdn-images-1.medium.com/max/2722/1*ENblXKMZOsPr4aIqMOhDFA.png)

so ***b50aded18e8af98761a91109a3027283dcd58cea80b152cdc5ce94470973473d*** is the md5 hash of the file and here we get our subflag for this question

![Subflag 8](https://cdn-images-1.medium.com/max/2000/1*M2sLUTNLpWAD-pmtqmam3w.png)*Subflag 8*

![](https://cdn-images-1.medium.com/max/2626/1*5uOY7rmK-GptLnRn66KPbA.png)

here we find the security vendor’s analysis so as we see Comodo calls this malware as ***Malware@#dvt1zjhgifb1 ***which will be our subflag and here we see the utility of virus total to get more details

![Subflag 9](https://cdn-images-1.medium.com/max/2000/1*pz-IDowQjnsIq2VOiHTThg.png)*Subflag 9*

To answer this question we can just see the historic from the details given by virus total and then we get the date of this malware which will be

***2020–07–24 04:07:50 UTC***

and here we solved all our Subflags and we are now going to find our main flag which will be the IP address used by the malware to communicates with

here we can also use Virus total that make it a little bit easy by a small navigation to the relations and we can scroll down to the graph summary proposed by this website

![](https://cdn-images-1.medium.com/max/2000/1*eb63x6gSghxzkR2jPQ8vjA.png)

here we see that this malware contacted 5 ips

![](https://cdn-images-1.medium.com/max/2000/1*jN9YVQzWrmW1AFKOCw9yKQ.png)

the active IP used by this malware is ***217.8.117.52 ***and here we got our main flag

![](https://cdn-images-1.medium.com/max/2000/1*nZt4ZfDShk-CJI3v9CzEEg.png)

## So the main flag is ***Securinets{217.8.117.52}***
