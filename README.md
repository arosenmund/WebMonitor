# WebMonitor
Repo for site route, dns and availability testing PowerShell based application. 


# What does this do?
Sites that collect sensitive data over the world wide web, do not always have the appropriate capability to deny person in the middle activity that can comrpomise your credentials, service availability, or data integrity.  Thats all of 3 of the big CIA!!! I know, that is why you should monitor for redirection of traffic from different parts of the world to your site.  If it generally takes 4 hops to get to a site and now it takes 20...that could be wierd BGP hijacking and you will get yellow or red alerts for that type of activity deviating from baseline.  If the DNS A records change, that could be DNS poisoning. 

## Currently Monitored
| Metric | Detection |
---       | --- 
| **Ping Latency** | A metric to identify potential loss of availability
| **Time to Live** | Returned ttl can indicate a differen service responding from the same location
| **Network Hops** | Devaition from verified baseline generates alerts
| **Route Consistency** | Calculated from a hash of the returend traceroute
| **DNS Entry Consistancy** | Calculated from a hash of the returned DNS entries for the domain

Let's talk about site security when it really matters!

Here is how you use it!

1. Download the repo.
2. Unzip if needed!
3. Edit "site_check_main.ps1" where the comments say "YOU NEED TO CHANGE THESE" you should change the variables pointing to the required folders in the downloaded and extracted folder.
4. Also, change the site to the site you would like to check!
5. Now run the whole scipt.
6. With the functions loaded, time to create a baseline, run create-baseline($site).
![create-baseline](create-baseline.png)
7. Kown good state recorded, run the continuous test with run-webtest($site)
![run-webtest](run-webtest.png)
8. Now non of this makes sense with out a live GUI to show all your friends, in a separate terminal in the webmonitor folder, run > ./php/php.exe -S localhost:8080
9. Browser to your website test, checking every 30 seconds or the specified interval for potential manipulation of traffic to and from your website.
![webmonitor](webmonitor.png)

That's it!

Improvments on the way:

- [ ] Condence workflow to one command that also launches the website.
- [ ] terraform deploy script to azure.
- [ ] Multi cloud warehouse hosting to compare deviations in traffic to a site from differnt parts of the world.
- [ ] Integrate with known BGP activity data.
