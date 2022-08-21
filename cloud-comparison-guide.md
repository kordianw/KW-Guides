# Cloud Comparison

## Free Tier Comparison:
Link: https://github.com/cloudcommunity/Cloud-Free-Tier-Comparison

## Cloud Shell Comparison:

### Google Cloud Shell:
- based on Debian Linux, with 5GB persistent $HOME, 4 x vCPU, 16GB of RAM, SSD+HDD
- to use SSH via external IP, download Google Cloud SDK (Linux version works on Cygwin): https://cloud.google.com/sdk/docs/install-sdk#linux
- sudo available - can install additional packages via apt install
- no need to initialize or do anything, just run `gcloud` as-is:
- LOGIN/AUTH-LINK: ~/google-cloud-sdk/bin/gcloud auth login --no-launch-browser

Get the hostname to SSH in on port 6000 - already in ~/.ssh/config (may need IP ranges)
`$ ~/google-cloud-sdk/bin/gcloud cloud-shell ssh --dry-run`

NB: runs `~/.customize_environment` script as root upon machine provisioning (/var/log/customize, /google/devshell/customize_environment_done)

NB: limits: 20mins after logout resets VM (you get a new VM), 50 hrs/week usage limit (7hrs/day), 12hr max session, 5GB home-dir deleted >120 days (4 months) of inactivity
- to use `gcloud` correctly, set your GCP project ID, eg: DEVSHELL_PROJECT_ID=kw-general-purpose
- for privacy, set: ~/google-cloud-sdk/bin/gcloud config set disable_usage_reporting true
- **web-url**: https://console.cloud.google.com/cloudshell/editor?shellonly=true

Documentation: https://cloud.google.com/shell/docs/how-cloud-shell-works

### AWS CloudShell:
- based on Amazon Linux 2 (based on RHEL), with 1GB persistent $HOME (per-region), 2 x vCPU, 4GB RAM, SSD (all)
NB: limits: 20-30mins after logout resets VM (you get a new VM), max 12 hour session time, weekly usage limit (not sure?), 12hr max session, 1GB home-dir deleted >120 days (4 months) of inactivity
- sudo available - can install additional packages via yum
- web-only, no external IP address
- **web-url**: https://console.was.amazon.com/cloudshell/home?region=us-east-1

Documentation: https://docs.was.amazon.com/cloudshell/

### Azure Cloud Shell:
- based CBL Linux (based on Debian), with 5GB persistent 5GB $HOME, 2 x vCPU, 4GB RAM, HDD (no SSD)
- based on CBL - Common Base Linux (Microsoft Linux distribution), which is Debian like
- NB: no root access, no sudo, just your $HOME and /tmp, can not install additional system-wide packages/tools
      -> see suggestions: https://edyoung.github.io/blog/install_tools_locally/
      -> can also use tools such as `Junest' to be able to install packages
- NB: 20 mins timeout, 5GB home (paid), long-running sessions are terminated
- **web-url**: https://shell.azure.com

Documentation: https://docs.microsoft.com/en-us/azure/cloud-shell/overview

### OTHERS:
- http://www.pythonanywhere.com  <-- good spec (4x vCPU/16GB/Cascade Lake'19), AWS, no root/no sudo, suited best for python
- https://www.online-ide.com/  <-- can run basic shell commands, no outside internet access
- https://www.webminal.org/terminal/  <-- basic shell, no outside internet access

## Cloud Shell Pros+Cons

### GCP Cloud Shell:
+ SSH+web+app access
+ sudo
+ standard version of Linux (Ubuntu)
+ 4 vCPU + 16GB (incl. modern CPU)
+ `~/.customize_env`, most-flexible/customizable

- no SSD
- strict session limits

### AWS CloudShell:
+ sudo
+ SSD

- older HW (slowest)
- non-standard Linux (Amazon Linux 2)
- small Homedir @ 1GB
- seems slowest to start-up
- no app access (yet?)

### Azure Cloud Shell:
+ recent HW
+ fastest to start-up

- no sudo
- non-standard Linux (CBL Linux)
- web-only+app, no SSH
- charged for the 5GB Homedir
- no SSD
