# CRLF-one-liner
A simple Bash one liner with aim to automate CRLF vulnerability scanning. This is an extremely helpful and practical One liner for Bug Hunters, which helps you find CRLF missconfiguration in every possible method. Simply replace the links in subdomains.txt with the URL you want to target. This will help you scan for CRLF vulnerability without the need of an external tool. What you have to do is to copy-and-paste the commands into your terminal and finger crossed for any possible CRLF.

## One-Liner Payload

`input='CRLF-one-liner/subdomains.txt';while IFS= read -r targets; do cat CRLF-one-liner/crlf_payloads.txt|xargs -I % sh -c "curl -vs --max-time 9 $targets/% 2>&1 |grep -q '< Set-Cookie: ?crlf'&& echo $targets '[+] is vulnerable with payload: '%>>crlf_results.txt||echo '[-] Not vulnerable: '$targets";done<$input`

## Installation

**Linux and Mac:**  

Download the github repository (from the /home directory):  
`git clone https://github.com/kleiton0x00/CRLF-one-liner.git`
  
**Windows:**  
https://github.com/kleiton0x00/CRLF-one-liner/archive/master.zip  
`Save it in Desktop`  
`Extract the zip`

## Usage
1. Open subdomains.txt and add the URL you want to scan.
2. Copy and paste the One-Liner Payload into your terminal

## Demo

![Demo CRLF one liner](https://i.imgur.com/A43KlGE.gif)

## NOTE
Make sure to execute the payload directly as you open the terminal. Don't change directory for any reason! However if your local directory doesn't match to the payload's directory, please feel free to manually change it.  
For example:  
From `input='Desktop/CRLF-one-liner/subdomains.txt'` to `input='another/path/to/subdomains.txt'`  
From `cat CRLF-one-liner/crlf_payloads.txt` to `cat path/to/crlf_payloads.txt`
