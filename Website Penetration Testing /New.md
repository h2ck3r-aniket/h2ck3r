#### TLD Enumeration:
```
crt domain | tee -a 
```
#### Subdomain Enumeration:
```
subfinder -dL domains.txt | httpx -mc 200 | tee urls.txt
```
```
subfinder -dL domains.txt | httpx -mc 400,401,403,404 | tee urls.txt
```
#### Urls Enumeration save into js.txt
```
cat urls.txt | waybackurls | tee waybackurls.txt
```
```
cat waybackurls.txt | httpx -mc 200 -ct | tee liveurls.txt
```
#### Json/Js Enumeration (COPY all urls and save into js.txt)
```
cat liveurls.txt | grep /javascript | json > js.txt
```
#### GitHub Targeting
