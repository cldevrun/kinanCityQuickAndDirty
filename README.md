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
Any site that sells domain names is fine. I just used namesilo.com to buy a cheap domain name & set up 2 DNS records.

#### Buy Anti-Captcha token
I just used the recommended anti-captcha.com site, forked over $5 to borrow their automatic captcha solvers, because I have little patience to solve them manually.

#### Buy Site Proxies like InstantProxy
I just instantproxies.com to get some residential ip proxies to get around PTC ip bans. Forked $10 USD over for 10 of them. If there are some invalid ones, you can kindly ask customer service to replace them.

#### Server setup
