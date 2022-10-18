
# DeadFace CTF (Steganography & Forensics)

Steganography

### The goodest boy

![Task description](https://cdn-images-1.medium.com/max/2000/1*ZK7QiDzr7KEuPQGG_1e0tA.png)*Task description*

This task is given as an image and as it tells there is an information hidden inside this image so we can think about extracting that information using steghide tool for this we need to get the passphrase let’s just try to pass our image throug strings and see if there is something usefull

![password](https://cdn-images-1.medium.com/max/2000/1*i3aI6bjsRAItoXKPgjmmbg.png)*password*

as we see in the strings we found already a password “borkbork” that can be the passphrase used to hide we try to use it inside the steghide command

![](https://cdn-images-1.medium.com/max/2000/1*GmO-PBxm_i2fOznWHcSPBA.png)

so the information hidden inside our image is a pdf file once we open it we get out flag “***flag{whos_A_g00d_boi_bork_bork}”***

### Eye Know , Do You ?

![Task description](https://cdn-images-1.medium.com/max/2000/1*r_VQN_0rmMaeNYLaIBKxBg.png)*Task description*

This task is also given as an image in this task i tried to use the website Aperisolve to get some help about the specific tool to use

![](https://cdn-images-1.medium.com/max/2106/1*U-MCUMQpwnKkx4nll0uaPg.png)

one of the results of aperisolve is this image and as we see we got a string that can be our flag so i put it in stegonline website to make it clear to figure out that string

![flag extracted](https://cdn-images-1.medium.com/max/2000/1*iiSuTDCGl4dqGNlL46uFkw.png)*flag extracted*

so our flag is ***flag{Deadface_Knows_All_Sees_All}***

### **Missing Home**

![Task description](https://cdn-images-1.medium.com/max/2000/1*8A9OFTdlbw94uKQcheOYZg.png)*Task description*

This task is given as an image and steghide is not working so we can extract all things hidden inside our image using foremost command

![](https://cdn-images-1.medium.com/max/2000/1*89wqEQMjJcOkhkUUQJKtDA.png)

the files hidden are so

![](https://cdn-images-1.medium.com/max/2296/1*EGtpeS550pWOwgtJgk0tKw.png)

as we see there is a flag in the description of the image in the left lets put the image inside cyberchef and see the result

![](https://cdn-images-1.medium.com/max/2000/1*Bwu9t0CVEEi44O7gYkZwAw.jpeg)

and that is our flag “***flag{s3cr3ts_don’T_stAy_bur13d_L0nG}***”

### **Scans**

![Task description](https://cdn-images-1.medium.com/max/2000/1*DvKGUhVFI4KnIUgWrCmjLg.png)*Task description*

this task is a traffic analysis given as a pcap file

![](https://cdn-images-1.medium.com/max/2732/1*ssqZIcjs7oW6q6sjJG5dZw.png)

analysing the ports and the packets we can figure that the scan is a SNYK and that is our flag ***“flag{snyk}”***

### **First Strike**

![Task description](https://cdn-images-1.medium.com/max/2000/1*OnC6XuAs-8su1VSBnaLhBQ.png)*Task description*

this task is given as a log file and it wants us to figure out the IP address of the attack origin

![](https://cdn-images-1.medium.com/max/2660/1*C4WIIGAhZBtfF9WAjQeyIw.png)

and our flag is ***flag{165.227.73.138}***

### Toolbox

![Task description](https://cdn-images-1.medium.com/max/2000/1*qZ27wdwmG0KVnzIPDMhRpg.png)*Task description*

to get the tool we can just find the date in the log file

![](https://cdn-images-1.medium.com/max/2552/1*jzAWxI6KbwIwZA5FYZFkiw.png)

so it is clear the tool is the nmap and the flag will be ***flag{nmap}***
