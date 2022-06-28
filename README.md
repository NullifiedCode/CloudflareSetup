# CloudflareSetup
My cloudflare setup for reducing malicious attacks. Also has a rule for VPN Providers & VPS Providers.


# First WAF Rule 
This one down below is used for embeding things inside discord. Say images/mp4 files or anything else.

![image](https://user-images.githubusercontent.com/79751099/176107272-3f021cab-81fb-4c4c-92cb-50e316fee5cb.png)

# Second WAF Rule
This second rule down below is used to block known VPS providers. (Vultr, Linode, OVH, DigitalOcean, A2 Hosting, Etc)
Keep in mind you can also add other ASN numbers to this list if you find any other providers/hosters.

![image](https://user-images.githubusercontent.com/79751099/176107599-d59d782c-97f8-4314-a42b-f2dac77034cc.png)

# Third WAF Rule
This third rule is by far the best one ive done. This one contains quite a few VPN providers ASN numbers. Meaning if you wanted
you can blacklist the users from your site on a VPN or throw them a Managed Challenge.

![image](https://user-images.githubusercontent.com/79751099/176107831-57be1fbc-becf-4edf-8f96-c8923ef67063.png)

# Last WAF Rule
This last rule is by far the most extensive and annoying long one. Being able to block most "Bad Actors" from accessing your site.
It blocks Tor, Unknown Countries, And Many other things that could bypass or even monitor your website. (Refering to https://check-host.net/?lang=en

>(cf.client.bot) or (http.user_agent contains "Cyotek") or (http.user_agent contains "python") or (http.user_agent contains "undefined") or (http.user_agent eq "Empty user agent") or (http.user_agent contains "HTTrack") or (http.user_agent contains "CheckHost") or (http.user_agent contains "Java") or (http.user_agent contains "curl") or (http.user_agent contains "RestSharp") or (http.user_agent contains "Ruby") or (http.user_agent contains "Nmap") or (http.user_agent eq "libwww") or (not http.request.version in {"HTTP/1.0" "HTTP/1.1" "HTTP/1.2" "HTTP/2" "HTTP/3"}) or (ip.geoip.country eq "T1") or (ip.geoip.country eq "XX") or (cf.threat_score ge 2) or (not http.request.method in {"GET"}) or (http.user_agent contains " Uptime-Kuma")

If you need help creating the rule you click on the edit expression then paste the code above into the box and press save.
![image](https://user-images.githubusercontent.com/79751099/176108597-768036cb-574c-4831-a575-2c643c1d25e1.png)


# Important
After all that is done. Make sure to go and disable **Bot Fight Mode** located under the Bots tab. Then order the ruleset exactly how I have mine.

![image](https://user-images.githubusercontent.com/79751099/176109008-b3efae73-878b-42c7-83eb-33a43165404d.png)
