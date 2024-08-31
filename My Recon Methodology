# My First Target is - Setu.co VDP

**Date:** 31 August 2024

**Author:** P.Hima Bindu


<!-- httpx -l subdomains.txt >> active_subdomains.txt 

httpx --status-code --title -l subdomains.txt > active_subdomains.txt -->

## 
- For My recon process I used Subfinder, Sublist3r and assetfinder for Subdomain enumaration 
  - First run subfinder and sublister by saving the results in a separate text files.
  - run assetfinder and also save the ouput to a text file
  - Merge all the files in a final_subdomains.txt file
  - Use httpx for filtering live hosts




```bash

subfinder -d setu.co >> subdomains.txt

python /usr/local/bin/Sublist3r/sublist3r.py -d setu.co >> subs2.txt
 

## Now run **assetfinder**


assetfinder --subs-only setu.co | tee -a assetfinder.txt


## Now merge all these files and save it in a final_subdomains.txt


cat subfinder.txt sublist3r.txt assetfinder.txt | sort -u | tee -a final_subdomains.txt


## Use **httpx** for http probing - live host discovery


cat final_subdomains.txt | httpx -sc -ip -server -title -p 80,443,8080,3000 | tee -a live_subs.txt

