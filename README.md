# CloudflareSetup
My cloudflare setup for reducing malicious attacks. Also has a rule for VPN Providers & VPS Providers.

# First WAF Rule (Optional Allow Rule)
This one down below is used for embeding things inside discord. Say images/mp4 files or anything else. This also works as a bypass. If you need other things to have full access for.

![image](https://user-images.githubusercontent.com/79751099/184986898-7b575ab8-a291-4ca7-897e-18b348d901b9.png)

# Second WAF Rule (Block Rule)
This last rule is by far the most extensive and annoying long one. Being able to block most "Bad Actors" from accessing your site.
It blocks Tor, Unknown Countries, And Many other things that could bypass or even monitor your website. (Refering to https://check-host.net/?lang=en

**This WAF Rule also blocks any other methods meaning POST, HEAD, Or any other do NOT work.** If you want to fix that just add it to the rule inside this rule to have GET, POST, PUT, ETC

>(cf.client.bot) or (http.user_agent contains "Cyotek") or (http.user_agent contains "python") or (http.user_agent contains "undefined") or (http.user_agent eq "Empty user agent") or (http.user_agent contains "HTTrack") or (http.user_agent contains "CheckHost") or (http.user_agent contains "Java") or (http.user_agent contains "curl") or (http.user_agent contains "RestSharp") or (http.user_agent contains "Ruby") or (http.user_agent contains "Nmap") or (http.user_agent eq "libwww") or (not http.request.version in {"HTTP/1.0" "HTTP/1.1" "HTTP/1.2" "HTTP/2" "HTTP/3"}) or (ip.geoip.country eq "T1") or (ip.geoip.country eq "XX") or (cf.threat_score ge 2) or (not http.request.method in {"GET" "POST"} and http.request.uri.path eq "/s") or (http.user_agent contains " Uptime-Kuma") or (http.user_agent contains "sitechecker") or (http.user_agent contains "axios") or (http.referer contains "youtube.com") or (http.referer contains "yahoo.com") or (http.referer contains "https://google.com") or (http.referer contains "https://check-host.net") or (http.referer contains "fbi.com") or (http.referer contains "bing.com")

If you need help creating the rule you click on the edit expression then paste the code above into the box and press save.
![image](https://user-images.githubusercontent.com/79751099/176108597-768036cb-574c-4831-a575-2c643c1d25e1.png)

# Third WAF Rule (Manage Challenge Rule)
This third rule is by far the best one ive done. This one contains quite a few VPN providers ASN numbers. Meaning if you wanted
you can blacklist the users from your site on a VPN or throw them a Managed Challenge.

![image](https://user-images.githubusercontent.com/79751099/176107831-57be1fbc-becf-4edf-8f96-c8923ef67063.png)

# Fourth WAF Rule (Block Rule - Optional - Highly Recommend)
This rule is for Malicious ASN'S refering to providers that allow/have a lot of malicious activity on their networks. This can also include various hosting providers.

![image](https://user-images.githubusercontent.com/79751099/184987490-f79e6e5e-75df-46a6-9e03-d92c7d71d23a.png)

# Fifth WAF Rule (Block Rule - Optional - Highly Recommend)
This rule is for Malicious ASN'S refering to providers that allow/have a lot of malicious activity on their networks. This can also include various hosting providers.

![image](https://user-images.githubusercontent.com/79751099/184988118-453e2895-add8-40ab-812b-df6dfcc80c65.png)

# Important (Have to Do)
After all that is done. Make sure to go and disable **Bot Fight Mode** located under the Bots tab. Then order the ruleset exactly how I have mine.

![image](https://user-images.githubusercontent.com/79751099/176111243-713b6bca-9929-47eb-9832-9fcad40440ce.png)

![image](https://user-images.githubusercontent.com/79751099/184988340-9b728dcf-7701-4d0b-a5c5-d2cb25181b67.png)


or If you have Cloudflare Pro or anything above it. Go and set the first top 2 options to **BLOCK** & also **Disable Javascript Detections**

![image](https://user-images.githubusercontent.com/79751099/176262127-5fca43fd-cd83-4857-8f20-7f076e8044c0.png)

# Last Reminder
**Disable the Option above otherwise you will still receive the DDoS attaack. Ive done testing and it works better without this.**

# End Result
![image](https://user-images.githubusercontent.com/79751099/184987251-5ba0b33e-ec2f-41f8-a7f1-1f7028f4814c.png)

The results from the image above (The ones showing the requests count) is running off of a $5 Linode VPS (Shared) and these rules above have solved the issues of L7 DDoS attacks. 

# Credits
Myself and this guy on this repo https://github.com/brianhama/bad-asn-list
