#### TLD Enumeration:
```
crt domain | tee -a
curl -s "https://crt.sh/?q=%25.citigroup.com&output=json" | jq -r '.[].name_value' | sed 's/\*\.//g' | httpx -title -silent | tee data
```
#### Subdomain Enumeration:
```
subfinder -dL domains.txt | httpx -mc 200 | tee urls.txt
subfinder -dL domains.txt | httpx -mc 400,401,403,404 | tee urls.txt
```
#### Urls Enumeration save into js.txt
```
cat urls.txt | waybackurls | tee waybackurls.txt
cat waybackurls.txt | httpx -mc 200 -ct | tee liveurls.txt
cat all-live.txt | gauplus -subs -b png,jpg,gif,jpeg,swf,woff,gif,svg -o allUrls.txt
```
#### Json/Js Enumeration (COPY all urls and save into js.txt)
```
cat liveurls.txt | grep /javascript | json > js.txt
```
#### GitHub Targeting


#### Nuclei
```
nuclei -iL liveurls.txt -t templates > vuln_nuclei.txt
```
#### Nikto
```
nikto -h liveurls.txt > vuln_nikto.txt
```
