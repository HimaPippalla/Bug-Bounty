# My First Target is - Setu.co VDP

**Date:** 31 August 2024

**Author:** P.Hima Bindu


<!-- httpx -l subdomains.txt >> active_subdomains.txt 

httpx --status-code --title -l subdomains.txt > active_subdomains.txt -->

## 
- For My recon process I used Subfinder, Sublist3r, assetfinder and amass for Subdomain enumaration 
  - First run subfinder and sublister by saving the results in a separate text files.
  - run assetfinder and amass also save the ouput to the text files
  - Merge all the files in a final_subdomains.txt file
  - Use httpx for filtering live hosts


### Run Subfinder & Sublist3r

```bash

subfinder -d example.com >> subdomains.txt

python /usr/local/bin/Sublist3r/sublist3r.py -d example.com >> subs2.txt
 
```

### Now run **assetfinder**

```bash

assetfinder --subs-only example.com | tee -a assetfinder.txt

```

### Now run **amass**

```bash

amass enum -passive -d example.com | tee -a amass.txt
```


### Now merge all these files and save it in a final_subdomains.txt

```bash

cat subfinder.txt sublist3r.txt assetfinder.txt amass.txt | sort -u | tee -a final_subdomains.txt

```

### Use **httpx** for http probing - live host discovery

```bash

cat final_subdomains.txt | httpx -sc -ip -server -title -p 80,443,8080,3000 | tee -a live_subs.txt
```

### OR

```bash

httpx -l final_subdomains.txt -sc -ip -title -p 80,443,8080,3000 | tee -a live_subs.txt 

