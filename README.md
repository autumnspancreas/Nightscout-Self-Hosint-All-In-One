# Nightscout-Self-Hosint-All-In-One
All-in-one guide to self-host Nightscout using an old computer or laptop
Still a work in Prograss. DO NOT USE YET!

## Create a free afraid.org account and choosing a DDNS hostname
Navigate your browser to https://freedns.afraid.org and click on the "Sign Up Free" button on the bottom. 
Enter your contact information, password, and email address. Complete the Captcha and click on "Send activation email" button

Click on the hypertext link in the verification email. 

Click on "Add a subdomain" in the center of the screen

Pick a public domain from the dropdown menu and then choose a subdomain (like 'nightscout'). Hint: Don't be content with the 7 domains they suggest, select "Many many more available..." on the bottom of the dropdown menu to search from 1000s of domains. 

Complete the Captcha and click "Save".

That's your domain name now! It automatically chooses the external IP Address that you using so it will work until your ISP changes your IP address. We will set up the DDNS renewal script on your Nightscout server once it's fully built. 

## Downloading the Linux ISO File and burning it into a USB Drive
Most Nightscout self-hosting tutorials that I've seen use Ubuntu as the Linux distribution. To add some diversity and because I really respect Red Hat as a company (they are fiercely supportive of open source projects and because of that, I have to give them credit). While there are a handful of Red Hat distributions (RHEL, Fedora, CentOS, Suse, Rocky, Oracle, etc) I am going to build CentOS Stream 8.

Navigate your browser to https://www.centos.org/centos-stream/. Select the "8" tab and then click on the architecture you are using (most likely x86_64, if you are using Raspberry Pi, it will probably be ARM64 although I can't confirm CentOS is compatible with RP). Don't worry about Cloud, Containters, or Vagrant links. After clicking on "x86_64" choose any mirror and then the .iso file that says "latest-DVD" in the name. The ISO file should automatically download. 

For Windows users download and install Rufus at https://rufus.ie/. Insert your USB drive into your computer. Start Rufus. Select your USB in the Device dropdown. Select Disk or ISO Image in the "Boot Selection" dropdown. Click "Select" and navigate to your downloaded ISO file. Click "Start".

Once the Rufus job is complete, pull the USB drive out of your Windows computer and insert it into the old computer or laptop that will become your Nightscout server. 


## Installing Linux on the old laptop or computer
## Configure port fowarding of 80, 1337, and 443 on the home router
This is difficult to explain in an all-in-one tutorial because the user interface of every router manufacturer is different, even between models of the same manufacturer. 

It might be best to google how to configure port forwarding with your router make and model, but he's a few that I know. 
### Asus Routers
Find your Gateway IP Address by clicking on the Windows Start button and typing "cmd", Select "Command Prompt". Within the command Prompt, type "ipconfig". Look for "Default Gateway", It should be some private IP address and usually ends in one (192.168.x.1 or 10.x.x.1). Type that IP address into your router. Log in using the credintials your created when you first set up the router. 

Click on WAN on the left panel. Click on the "Virtual Server / Port Forwarding" Tab

-First Port-
Click on "Add Profile"
Service Name: http
Protocol: tcp
External Port: 80
Internal Port: 80
Internal IP Address: <The IP Address of your new Nightscout server>
Click "OK"

 -Second Port-
Click on "Add Profile"
Service Name: https
Protocol: tcp
External Port: 443
Internal Port: 443
Internal IP Address: <The IP Address of your new Nightscout server>
Click "OK"

 -Third Port-
Click on "Add Profile"
Service Name: L33T
Protocol: tcp
External Port: 1337
Internal Port: 1337
Internal IP Address: <The IP Address of your new Nightscout server>
Click "OK"

## Installing Nightscout onto Linux server
## Installing Nginx and Certbot
## Installing the afraid.org DDNS agent onto Linux server
