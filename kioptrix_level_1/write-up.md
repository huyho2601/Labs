**Reconnasance**

First, I identified the the IP address of the machine by `sudo arp-scan -l`. Note that since I was running running normal user, i needed to use `sudo`.

`arp-scan -l` allowed me to scan all IPs on same network. This returned the IP address of Kioptrix machine, which is `192.168.85.130`

![alt text](image.png)

Once the IP address was identified, I ran `nmap -T4 -p- -A 192.168.85.130` to scan open ports as well as detect possible vulnerabilities. Note that `-T4` indicates aggressive speed scan, `-p-` denotes all ports scanning, `-A` indicates scanning all

![alt text](image-1.png)

Of all the port I obtained, ports 22, 80, 139, 443 appeared to be promising.

**Inspecting port 80, 443**
The information gained from these 2 ports is that the server is running on **Apache 1.3.20 (Unix)**, **(Red-Hat/Linux) mod_ssl/2.8.4** and **OpenSSL/0.9.6b**.

I checked both http://192.168.85.130/ and https://192.168.85.130/ for port 80 and 443, respectively. However, only port 80 resulted in working interface.

![alt text](<Screenshot 2026-07-14 151752.png>)

Nevertheless, I could not find anything useful here

Next, since this is web server, I ran `nikto -h http://192.168.85.130` to scan the web server vulnerability. 

![alt text](image-2.png)

Here, I found out what Apache 1.3.20 and mod_ssl 2.8.4 are vulnerable to, e.g. buffer overflow 



**Inspecting port 139**
