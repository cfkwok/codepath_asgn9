# Project 10 - Honeypot

Time spent: **1** hours spent in total

> Objective: Setup a honeypot and provide a working demonstration of its features.

### Required: Overview & Setup

- [x] A basic writeup (250-500 words) on the `README.md` desribing the overall approach, resources/tools used, findings
This is a simple honeypot made for WordPress called HonnyPotter. The main idea is that it logs any failed attempts for logging in. There are many uses for this, as it can detect if there is anyone who is trying to steal accounts, do SQLI, or any other vulnerbilities that can occur with an input text box. 

- [x] A specific, reproducible honeypot setup, ideally automated. There are several possibilities for this:
	- A Vagrantfile or Dockerfile which provisions the honeypot as a VM or container
	- A bash script that installs and configures the honeypot for a specific OS
	- Alternatively, **detailed** notes added to the `README.md` regarding the setup, requirements, features, etc.
To reproduce this honeypot, go to your wp site as an admin and go to plugins. Search for HonnyPotter and install, then activate it. Make some failed attempts at logging in. On the admin account, go to Settings -> HonnyPotter and there will be a link to the output log for the failed login attempts. 

### Required: Demonstration

- [x] A basic writeup of the attack (what offensive tools were used, what specifically was detected by the honeypot)
No real "attacks" would trigger this honeypot, but any kind of failed login attempts, even if they were typos. However, with HonnyPotter, an admin can spot whether or not there is anyone trying to do SQLI, or even pulling a rainbow table on wp accounts from the logs. 
- [x] An example of the data captured by the honeypot (example: IDS logs including IP, request paths, alerts triggered)
Logs of HonnyPotter:
au: 2017-04-05 23:43:19 - moomoo:adlkasdlkasd
wp: 2017-04-05 23:43:19 - moomoo:adlkasdlkasd
wp: 2017-04-05 23:43:23 - cfkwok:asdlkasdlkjsad
au: 2017-04-05 23:45:39 - \') or \'1\'=\'1--:\') or \'1\'=\'1--
wp: 2017-04-05 23:45:39 - \') or \'1\'=\'1--:\') or \'1\'=\'1--
au: 2017-04-05 23:45:56 - \' or 1=1--:\' or 1=1--
wp: 2017-04-05 23:45:56 - \' or 1=1--:\' or 1=1--
au: 2017-04-05 23:46:05 - \' UNION SELECT 1, \'anotheruser\', \'doesnt matter\', 1--:\' UNION SELECT 1, \'anotheruser\', \'doesnt matter\', 1--
wp: 2017-04-05 23:46:05 - \' UNION SELECT 1, \'anotheruser\', \'doesnt matter\', 1--:\' UNION SELECT 1, \'anotheruser\', \'doesnt matter\', 1--
- [x] A screen-cap of the attack being conducted
http://imgur.com/ofFBqdx

    
### Optional: Features
- Honeypot
	- [ ] HTTPS enabled (self-signed SSL cert)
	- [ ] A web application with both authenticated and unauthenticated footprint
	- [ ] Database back-end
	- [ ] Custom exploits (example: intentionally added SQLI vulnerabilities)
	- [ ] Custom traps (example: modified version of known vulnerability to prevent full exploitation)
	- [ ] Custom IDS alert (example: email sent when footprinting detected)
	- [ ] Custom incident response (example: IDS alert triggers added firewall rule to block an IP)
- Demonstration
	- [ ] Additional attack demos/writeups
	- [ ] Captured malicious payload
	- [ ] Enhanced logging of exploit post-exploit activity (example: attacker-initiated commands captured and logged)