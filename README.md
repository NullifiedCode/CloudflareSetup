# CloudflareSetup
My cloudflare setup for reducing malicious attacks. Also has a rule for VPN Providers & VPS Providers.


# First WAF Rule (Optional Allow Rule)
This one down below is used for embeding things inside discord. Say images/mp4 files or anything else.

![image](https://user-images.githubusercontent.com/79751099/176114953-4e54d97d-6548-4e3d-9c6b-337a25130288.png)

# Second WAF Rule (Block Rule)
This second rule down below is used to block known VPS providers. (Vultr, Linode, OVH, DigitalOcean, A2 Hosting, Etc)
Keep in mind you can also add other ASN numbers to this list if you find any other providers/hosters.

![image](https://user-images.githubusercontent.com/79751099/176107599-d59d782c-97f8-4314-a42b-f2dac77034cc.png)

# Third WAF Rule (Manage Challenge Rule)
This third rule is by far the best one ive done. This one contains quite a few VPN providers ASN numbers. Meaning if you wanted
you can blacklist the users from your site on a VPN or throw them a Managed Challenge.

![image](https://user-images.githubusercontent.com/79751099/176107831-57be1fbc-becf-4edf-8f96-c8923ef67063.png)

# Last WAF Rule (Block Rule)
This last rule is by far the most extensive and annoying long one. Being able to block most "Bad Actors" from accessing your site.
It blocks Tor, Unknown Countries, And Many other things that could bypass or even monitor your website. (Refering to https://check-host.net/?lang=en

**This WAF Rule also blocks any other methods meaning POST, HEAD, Or any other do NOT work.** If you want to fix that just add it to the rule inside this rule to have GET, POST, PUT, ETC

>(cf.client.bot) or (http.user_agent contains "Cyotek") or (http.user_agent contains "python") or (http.user_agent contains "undefined") or (http.user_agent eq "Empty user agent") or (http.user_agent contains "HTTrack") or (http.user_agent contains "CheckHost") or (http.user_agent contains "Java") or (http.user_agent contains "curl") or (http.user_agent contains "RestSharp") or (http.user_agent contains "Ruby") or (http.user_agent contains "Nmap") or (http.user_agent eq "libwww") or (not http.request.version in {"HTTP/1.0" "HTTP/1.1" "HTTP/1.2" "HTTP/2" "HTTP/3"}) or (ip.geoip.country eq "T1") or (ip.geoip.country eq "XX") or (cf.threat_score ge 2) or (not http.request.method in {"GET"}) or (http.user_agent contains " Uptime-Kuma")

If you need help creating the rule you click on the edit expression then paste the code above into the box and press save.
![image](https://user-images.githubusercontent.com/79751099/176108597-768036cb-574c-4831-a575-2c643c1d25e1.png)

# Important
After all that is done. Make sure to go and disable **Bot Fight Mode** located under the Bots tab. Then order the ruleset exactly how I have mine.

![image](https://user-images.githubusercontent.com/79751099/176260531-eddea1ea-dab0-486f-afed-f6e1870ee7c2.png)

# Last Reminder
**Disable This Option otherwise you will still receive the DDoS attaack. Ive done testing and it works better without this.**

![image](https://user-images.githubusercontent.com/79751099/176111243-713b6bca-9929-47eb-9832-9fcad40440ce.png)


# End Result
The results from the image above (The ones showing the requests count) is running off of a $5 Linode VPS (Shared) and these rules above have solved the issues of L7 DDoS attacks. 
