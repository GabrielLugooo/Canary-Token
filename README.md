<img align="center" src="https://i.imgur.com/ZgHWFhw.png" alt="gabriellugo" />

# CANARY TOKEN

<a href="https://github.com/GabrielLugooo/Canary-Token" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.shields.io/badge/English%20Canary%20Token-000000" alt="English Canary" /></a>
<a href="https://github.com/GabrielLugooo/Canary-Token/blob/main/README%20Spanish.md" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.shields.io/badge/Spanish%20Canary%20Token-green" alt="Spanish Canary" /></a>

## Objectives

This document explains, from a defensive and conceptual perspective, what a website copier like HTTrack is, how attackers exploit it for copying and phishing, and how to defend against it using Canary Tokens and a Canary Token Server.

Generally speaking, website copiers pose a phishing threat, and we recommend detection and mitigation measures (with a special focus on Canary Tokens).

This repository is for informational and defense purposes only. It does not contain (nor does it request) instructions for carrying out attacks.

It is intended for security teams, web administrators, and developers.

## Skills Learned

- Advanced understanding of HTTrack Website Copier concepts and their practical operation.

- Advanced understanding of Canary Token concepts and their practical application.

- Proficiency in using a Canary Token Server.

- Ability to generate and recognize signatures and attack patterns.

- Greater awareness of security vulnerabilities.

- Development of critical thinking and problem-solving skills in cybersecurity.

## Tools Used

![Static Badge](https://img.shields.io/badge/HTTracks-000000?logo=github&logoSize=auto)
![Static Badge](https://img.shields.io/badge/CanaryToken-000000?logo=github&logoSize=auto)
![Static Badge](https://img.shields.io/badge/CanaryServer-000000?logo=github&logoSize=auto)

- HTTrack: Website copier/offline browser tool.

- CanaryToken analysis tool (tripwires).

- Private CanaryToken server to detect unauthorized access and cloned links.

## What is HTTrack Website Copier?

A website copier (like HTTrack) is a utility that downloads pages, images, and resources from a website to recreate it locally or on another server. It's legitimately used for archiving or offline browsing, but this same capability can facilitate the creation of website replicas.

### Attack Layout

#### General Attack Layout

<img align="center" src="assets/HttrackLayout.jpg" alt="Httrack Layout" />

#### HTTrack website

<img align="center" src="assets/HttrackWeb1.jpg" alt="Httrack Web" />

#### Download from HTTrack

<img align="center" src="assets/HttrackWeb2.jpg" alt="Httrack Download" />

#### Initial setup

<img align="center" src="assets/HttrackSetup1.jpg" alt="Httrack Setup" />

#### Name the project

<img align="center" src="assets/HttrackSetup2.jpg" alt="Httrack Project Name" />

#### Copy _REAL_ website address

<img align="center" src="assets/WellsFargoReal.jpg" alt="Httrack Copy Dir" />

#### Paste the address of the website to copy

<img align="center" src="assets/HttrackSetup3.jpg" alt="Httrack Paste Dir" />

#### _Mirroring_ or cloning operation

<img align="center" src="assets/HttrackSetup4.jpg" alt="Httrack Mirroring init" />

#### Mirroring operation completed

<img align="center" src="assets/HttrackSetup5.jpg" alt="Httrack Mirroring Finish" />

#### Web result _FAKE_ (see HHTTP on Local)

<img align="center" src="assets/WellsFargoFake.jpg" alt="Httrack Results" />

## Canarytokens: What are they and why do they help?

Canarytokens are simple "tripwires" (links, documents, DNS names, fake API keys, etc.) that, when accessed or executed, trigger an alert notifying you that something suspicious has occurred. They are a cost-effective way to detect malicious activity early.

Your own server: Thinkst publishes tools and Docker images to run your own Canarytoken server—useful for avoiding reliance on public services and for scalability/privacy.

### Initial Defense Layout

#### Threat Target

<img align="center" src="assets/HttrackLayout2.jpg" alt="Httrack Target" />

#### Select the cloned website token on the Canary website

<img align="center" src="assets/CanaryWeb1.jpg" alt="Canary Web Select Token" />

#### In the cloned website token field, enter the requested information:

- Email for alerts
- Token name
- Website to protect from cloning

<img align="center" src="assets/CanaryWeb2.jpg" alt="Canary Token Info" />

#### Copy the token's JavaScript

<img align="center" src="assets/CanaryWeb3.jpg" alt="Canary Token JavaScript" />

#### Open the index.html of the REAL website

<img align="center" src="assets/CanaryTokenJS1.jpg" alt="Canary Token Javascript" />

#### Paste the token's Javascript (don't forget the <script></script> tags)

<img align="center" src="assets/CanaryTokenJS2.jpg" alt="Canary Token Javascript" />

#### Token Triggering

- If someone clones the website, the token will be triggered, and we will receive an email alert with basic details:

<img align="center" src="assets/CanaryTokenJS4.jpg" alt="Canary Token Mail" />

- We can also see the alert trigger on the CanaryToken website and more details such as the location

of the threat:

<img align="center" src="assets/CanaryTokenJS5.jpg" alt="Canary Token Map" />

#### Obfuscating the JavaScript Token

- If the threat inspects the website's index.html before cloning, it can determine that the website contains a Canary Token. To strengthen security and make the token invisible, we proceed with obfuscation of the .JS file using the website obfuscator.io:

<img align="center" src="assets/CanaryTokenJS6.jpg" alt="JavaScript obf 1 Token" />

- Once executed (click the obfuscate button), copy the obfuscated Javascript token. It would look something like this:

<img align="center" src="assets/CanaryTokenJS7.jpg" alt="Javascript obf 2 Token" />

- Paste the obfuscated Javascript token into the index.html of the website:

<img align="center" src="assets/CanaryTokenJS8.jpg" alt="Token Javascript obf 3" />

#### Pinging the canarytokens.com website

- In CMD, we proceed to ping the canarytokens.com website. This will give us the server's IP address, allowing us to mask the canarytokens.com domain:

- We copy the IP address and paste it as shown in the image ('HTTP://52.18.63.80/') into the obfuscated token, in the index.html file where the canarytokens.com domain was previously located.

<img align="center" src="assets/CanaryTokenJS9.jpg" alt="Canary Ping" />

#### Hiding the final token

- Finally, it should look something like this if a threat inspects the code of the index.html file of the real website:

<img align="center" src="assets/CanaryTokenJS10.jpg" alt="Canary Token Final" />

## CanaryToken Private Server for Enhanced Security

### Dockerized

- You can follow the instructions in the Canarytokens/Thinkst repository on GitHub.

https://github.com/thinkst/canarytokens

#### Installing Docker for Linux

- Follow the instructions to install Docker for Linux from the repository.

Open a virtual machine on your Linux server; in this example, Ubuntu.

- Update Docker package:

<img align="center" src="assets/DockerLinux2.jpg" alt="Docker Linux 2" />

- Install the Docker package:

<img align="center" src="assets/DockerLinux3.jpg" alt="Docker Linux 3" />

- Add the official Docker GPG Key:

<img align="center" src="assets/DockerLinux4.jpg" alt="Docker Linux 4" />

- Configure the stable Docker repository:

<img align="center" src="assets/DockerLinux5.jpg" alt="Docker Linux 5" />

- Update Docker Engine:

<img align="center" src="assets/DockerLinux6.jpg" alt="Docker Linux 6" />

- Install Docker Engine:

<img align="center" src="assets/DockerLinux7.jpg" alt="Docker Linux 7" />

- Verify that Docker Engine was installed correctly by running the Hello-World image:

<img align="center" src="assets/DockerLinux8.jpg" alt="Docker Linux 8" />

#### Clone GitHub from Canary

- Git clone:

<img align="center" src="assets/CanaryGithubClone1.jpg" alt="Canary Clone 1" />

- Position yourself within cd canarytokens-docker:

<img align="center" src="assets/CanaryGithubClone2.jpg" alt="Canary Clone 2" />

- Install Python (in this case the version python3 with pip)
  give [Y]:

<img align="center" src="assets/CanaryGithubClone3.jpg" alt="Canary Clone 3" />

#### Install Docker Compose:

- Install Python-dev (in this case python3-dev):

<img align="center" src="assets/DockerCompose1.jpg" alt="Docker Compose 1" />

- Install -dev libraries:

<img align="center" src="assets/DockerCompose2.jpg" alt="Docker Compose 2" />

- Install Docker Compose:

<img align="center" src="assets/DockerCompose3.jpg" alt="Docker Compose 3" />

#### Rename Files:

- List files in Use `/canarytokens-docker` with `_ls_` and rename the following files:
- `switchboard.env.dist` to `switchboard.env`
- `frontend.env.dist` to `frontend.env`

<img align="center" src="assets/DockerRename1.jpg" alt="Docker Rename 1" />

- Open `frontend.env`:

<img align="center" src="assets/DockerRename2.jpg" alt="Docker Rename 2" />

- Configure your domains so that their nameservers point to the public IP address of the Docker host. This requires a change to your domain registry. Simply modifying the DNS records in the file zone is not enough. You will need an A record for your domain that points to your public IP address.

- Enter the value CANARY_DOMAINS= the IP/Domain to protect
- Enter the value CANARY_NXDOMAINS= for PDF Tokens only
- If you have a GOOGLE_API_KEY=, enter it as well
- Save

<img align="center" src="assets/DockerRename3.jpg" alt="Docker Rename 3" />

<img align="center" src="assets/DockerRename4.jpg" alt="Docker Rename 4" />

<img align="center" src="assets/DockerRename5.jpg" alt="Docker Rename 5" />

- Open switchboard.env
- Uncomment CANARY_PUBLIC_IP= or CANARY_PUBLIC_DOMAIN and set it with the IP/Domain
- CANARY_ALERT_EMAIL= Email to receive alerts
- CANARY_ALERT_FROM_DISPLAY = Message to receive in alerts
- CANARY_ALERT_EMAIL_SUBJECT = Subject of alert emails

<img align="center" src="assets/DockerRename6.jpg" alt="Docker Rename 6" />

- Download and launch the Docker Compose images:

<img align="center" src="assets/DockerRename7.jpg" alt="Docker Rename 7" />

#### Ports

- Check the active ports (Docker servers)

<img align="center" src="assets/DockerPorts1.jpg" alt="Docker Ports 1" />

#### Canarytoken Frontend

- Run `ifconfig` to see the IP address where the Canary frontend is running:

<img align="center" <img align="center" src="assets/DockerPorts2a.jpg" alt="Docker Ports 2a" />

<img align="center" src="assets/DockerPorts2.jpg" alt="Docker Ports 2" />

#### Tokenization Process (Repeat SAME as per Initial Defense Layout)

- Generate the token .js for the cloned website:
- Copy the token .js

<img align="center" src="assets/DockerPorts3.jpg" alt="Docker Ports 3" />

- Open the index.html of the website to be protected and paste the token .js
- Save

<img align="center" src="assets/DockerPorts4.jpg" alt="Docker Ports 4" />

- Test the alert trigger in our Canarytokens Docker

<img align="center" src="assets/DockerPorts5.jpg" alt="Docker Ports 5" />

- Obfuscate the .JS file using obfuscator.io
- Copy the obfuscated .JS token

<img align="center" src="assets/DockerPorts6.jpg" alt="Docker Ports 6" />

- Open the index.html file of the website to be protected and replace the previous .JS file with the obfuscated token .JS file
- Save

<img align="center" src="assets/DockerPorts7.jpg" alt="Docker Ports 7" />

- That's it!

# Recommended Defense Strategy (practical summary, no commands):

- Inventory and prioritization: identify critical assets (login pages, key repositories, internal portals).

- Place canary tokens in locations that are “attractive” to an attacker: login pages not publicly accessible, “secret.txt” files in administrative paths, environment variables in repositories (as fake tokens).

_My favorite: use tokens on sensitive pages and in GitHub secrets to detect exfiltration_

- Private Canary Token Server: deploy if you need control and privacy; use official Docker images as a starting point.

- Monitoring and alerts: integrate token notifications with your SIEM, Slack/Teams, or a quick-response email system.

- Additional web hygiene: strict HTTPS, HSTS, certificate validation, DMARC/SPF/DKIM for email, and a Content Security Policy (CSP) to reduce injection risks.

- Education and playbooks: Train users on how to verify domains and have a playbook for responding to detected phishing.

## Specific detection of clones/phishing (what to look for):

- Requests to suspicious hosts that return content identical to yours.

- Canary tokens triggered from unusual IPs/ASNs or from countries where you don't operate.

- Multiple authentication attempts to accounts from the cloned URL (if you can correlate them).

- DMARC monitoring/email forensics to detect mailings with similar domains.

_(These points are indicative—design them according to your monitoring capabilities.)_

## Response upon detection (checklist):

- Confirm the phishing attempt: Validate the triggering token and its context (IP, UA, referrer).

- Capture evidence (logs, pcap if applicable, screenshots).

- Block the URL/hosting where the clone is located (report to the provider/registrar).

- Notify legal/PR teams if there is a data breach or reputational risk.

- Rotate potentially compromised credentials and enforce MFA where applicable.

- Review and strengthen controls where the incident exploited a weakness.

## Best practices to reduce the phishing surface:

- Enforce mandatory MFA for sensitive access.

- Implement DMARC/SPF/DKIM to mitigate email spoofing.

- Enforce HSTS, valid certificates, and certificate pinning where practical.

- Review asset exposure in public repositories (secrets scanning).

- Employ canary detections in repositories and configurations.

_(My favorite: a fake AWS API key token on GitHub to detect leaks)_

## Ethical and legal considerations

- Do not use honeypot/canary techniques that may violate local laws (e.g., collecting personal data without notification).

- Coordinate with the legal team before deploying sensors that interact with external users.
- Canary tokens should not be used for "backhacking."

## Useful Resources (Official Readings)

- HTTrack — official site explaining what it is and its legitimate uses.

https://www.httrack.com/

- Canarytokens / Thinkst (repository and documentation).

https://github.com/thinkst/canarytokens

- Canarytokens.org — public page and generator.

https://canarytokens.org/nest/

- Summary article on website downloaders and general risks.

https://www.lifewire.com/how-to-download-a-website-for-offline-reading-4769529

### Limitations

Canary token it's just for educational purpose under the MIT License.

---

<h3 align="left">Connect with me</h3>

<p align="left">
<a href="https://www.youtube.com/@gabriellugooo" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.icons8.com/?size=50&id=55200&format=png" alt="@gabriellugooo" height="40" width="40" /></a>
<a href="http://www.tiktok.com/@gabriellugooo" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.icons8.com/?size=50&id=118638&format=png" alt="@gabriellugooo" height="40" width="40" /></a>
<a href="https://instagram.com/lugooogabriel" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.icons8.com/?size=50&id=32309&format=png" alt="lugooogabriel" height="40" width="40" /></a>
<a href="https://twitter.com/gabriellugo__" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.icons8.com/?size=50&id=phOKFKYpe00C&format=png" alt="gabriellugo__" height="40" width="40" /></a>
<a href="https://www.linkedin.com/in/hernando-gabriel-lugo" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.icons8.com/?size=50&id=8808&format=png" alt="hernando-gabriel-lugo" height="40" width="40" /></a>
<a href="https://github.com/GabrielLugooo" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.icons8.com/?size=80&id=AngkmzgE6d3E&format=png" alt="gabriellugooo" height="34" width="34" /></a>
<a href="mailto:lugohernandogabriel@gmail.com"> <img align="center" src="https://img.icons8.com/?size=50&id=38036&format=png" alt="lugohernandogabriel@gmail.com" height="40" width="40" /></a>
<a href="https://linktr.ee/gabriellugooo" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://simpleicons.org/icons/linktree.svg" alt="gabriellugooo" height="40" width="40" /></a>
</p>

<p align="left">
<a href="https://github.com/GabrielLugooo/GabrielLugooo/blob/main/README.md" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.shields.io/badge/English%20Version-000000" alt="English Version" /></a>
<a href="https://github.com/GabrielLugooo/GabrielLugooo/blob/main/Readme%20Spanish.md" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.shields.io/badge/Spanish%20Version-Green" alt="Spanish Version" /></a>
</p>

<a href="https://linktr.ee/gabriellugooo" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.shields.io/badge/Credits-Gabriel%20Lugo-green" alt="Credits" /></a>
<img align="center" src="https://komarev.com/ghpvc/?username=GabrielLugoo&label=Profile%20views&color=green&base=2000" alt="GabrielLugooo" />
<a href="" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.shields.io/badge/License-MIT-green" alt="Last Edited" /></a>

```

```
