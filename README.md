# kinanCityQuickAndDirty
Getting Kinan City PTC Account Generator up quick and dirty using $$

__Disclaimer__: This guide should be working as of 9/6/2022 and is my interpretation of a quick & dirty way just to get it running. I didn't really care much about security considerations, I just want it running & was willing to spend $$ to get it done. Costs are reflective on what I paid at the time.

## Table of Contents
* [Costs Breakdown](https://github.com/cldevrun/kinanCityQuickAndDirty/blob/main/README.md#costs-breakdown)
* [Steps to Get it Running](https://github.com/cldevrun/kinanCityQuickAndDirty/blob/main/README.md#steps-to-get-it-running)
   * [Buy email domain name & set up DNS records](https://github.com/cldevrun/kinanCityQuickAndDirty/blob/main/README.md#buy-email-domain-name--set-up-dns-records)
   * [Buy Anti-Captcha token](https://github.com/cldevrun/kinanCityQuickAndDirty/blob/main/README.md#buy-anti-captcha-token)
   * [Buy Site Proxies like InstantProxy](https://github.com/cldevrun/kinanCityQuickAndDirty/blob/main/README.md#buy-site-proxies-like-instantproxy)
   * [Server setup](https://github.com/cldevrun/kinanCityQuickAndDirty/blob/main/README.md#server-setup)


### Costs Breakdown
- Total Costs (~ $15-30 USD)
- Server (in my case Azure on Ubuntu 20, but any should work fine, program takes around roughly 2-3GB) (~$5-10 USD)
- Email domain name from namesilo.com (~$2 USD for a your custom \*.top domain name which lasts 1 year)
- Anti-Captcha service from anti-captcha.com (~$5 USD)
- Site Proxies from instantproxies.com (~$10 USD)

![image](https://user-images.githubusercontent.com/41696406/188574182-b2f9d615-6a32-479c-8ab5-f0cd04362389.png)

### Steps to Get it Running

#### Buy email domain name & set up DNS records
Any site that sells domain names is fine. I just used namesilo.com to buy a cheap domain name & set up 2 DNS records (1 A & 1 MX). For me, I just configured an A record to set my hostname to my server ip address & configured an MX record to set my hostname to my new domain name within my DNS manager. Records will take 15-30 minutes to propogate. Use mxtoolbox.com to know when your email domain records are up. Jot down the new website name because you will need it when setting up Kinan on your server.

<img width="728" alt="arecordkinan" src="https://user-images.githubusercontent.com/41696406/188580569-124a8e06-2176-4d40-b669-3e13673630f2.png">
<img width="701" alt="mxrecordkinan" src="https://user-images.githubusercontent.com/41696406/188581743-34c98c47-8bb4-42ef-a345-d25ab8bbe281.png">

#### Buy Anti-Captcha token
I just used the recommended anti-captcha.com site, forked over $5 to borrow their automatic captcha solvers, because I have little patience to solve them manually.
After getting an account key on the site, all you just need to do is to activate it. Jot the account key down somewhere because you will need it for server setup.

#### Buy Site Proxies like InstantProxy
I just instantproxies.com to get some residential ip proxies to get around PTC ip bans. Forked $10 USD over for 10 of them. If there are some invalid ones, you can kindly ask customer service to replace them. Take note of your given proxies in the proxy control panel, as well as authorize your server ip to allow your server to use those proxies.

#### Server setup
The only other thing I installed besides Kinan City related stuff is just Java. I just followed this Digital Ocean [guide](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-22-04). Just ran these 2 commands & went on to configure Kinan.
```
sudo apt install default-jre
sudo apt install default-jdk
```
Get the latest releases for Kinan City Core and Kinan City Email, & scp or wget or do whatever to get them inside the server **within differnt** directories, because each of them will read different properties.config files, each with different contents as described below.
For the mail server config file, you really just need to change 2 lines, one for the proxy ip the email server will need, and the other the custom email domain name, which is just the new $2 DNS obtained from namesilo.com like __kjsdhfsdkj.top__

![image](https://user-images.githubusercontent.com/41696406/188588985-5a8e98b2-6375-4961-9a8c-ba03e857e7bd.png)
 For the core server config file, only 3 fields I ended up modifying, the captcha.provider to antiCaptcha, key to my own captcha key with no spaces between, proxies to my list of proxies newly obtained from instantproxies.com
 ![image](https://user-images.githubusercontent.com/41696406/188589671-47854ab4-3c45-4940-ace1-38cb0b49b6b1.png)

After configuring the properties files for both Kinan core server and mail server, run the mail server
```
java -jar kinancity-mail-2.1.6-SNAPSHOT.jar
# if run as background, use nohup
nohup java -jar kinancity-mail-2.1.6-SNAPSHOT.jar &
```
then run the core server to generate your PTC accounts
```
java -jar kinancity-core-2.1.6-SNAPSHOT.jar -m <Your_user_defined_header>@<email_domain_name> -f vb***gh -p <your_password> -c <number_of_ptc_u_want>
```

For me, it was best to do a dry run to check if proxies were working first
```
To create 1 account 
java -jar kinancity-core-2.1.6-SNAPSHOT.jar  -user <ptc_username> -m <user_defined_email_username>@<user_defined_email_domain_name> -p <user_defined_password>
```
