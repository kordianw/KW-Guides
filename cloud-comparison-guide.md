# Cloud Comparison

## Free Tier Comparison:

### AWS

Link: https://was.amazon.com/free

12-Months Free:
- Many services, incl. EC2, only for new accounts
  - t2.micro / t3.micro, 750 hrs/month, free for only 12 months

Always-Free:
- Amazon DynamoDB (NoSQL): 25 GB of storage
- AWS Lambda (FaaS): 1 Million free requests per month
- Amazon SNS: 1 Million publishes (Mobile Push)

- US-EAST: nearest DC is in Ashburn, VA

Pricing: easy curl command:
- curl -L 'ec2.shop?filter=.nano'
- curl -L 'ec2.shop?filter=.small'

Link: https://github.com/cloudcommunity/Cloud-Free-Tier-Comparison

### AZURE

Link: https://azure.microsoft.com/en-us/free

12-Months Free:
- Many services, incl. VMs, only for new accounts
- $200 free credit for 30 days

Always-Free:
- Azure Cosmos DB (1,000 request units per-second provisioned throughput with 25 GB storage)
- Azure App Service (10 web, mobile, or API apps with 1 GB storage)
- Azure Functions (1 million requests)

- US-EAST: nearest DC is in Ashburn, VA

### GCP

Link: https://cloud.google.com/free/docs/gcp-free-tier

90-Days Free:
- 90-day, $300 Free Trial for new accounts only

Always-Free:
- Compute VM "e2-micro": 2 vCPU (0.25 cores committed), 1G RAM, 30 GB persistent-disk (only on us-west1, us-central1 and us-east1)
  - approximate value: ~$6.11/month
  - closest free-tier DC is us-east1 (S.Carolina), then us-central1 (Iowa)
  - comes with 1 free external public IP address
- 5GB Google Cloud Storage: only on us-west1, us-central1 & us-east1
- 5 GB-month snapshot storage
- 1GB of network egress (except China and Australia)
- ...many others, see: https://cloud.google.com/free/docs/free-cloud-features#free-tier

- US-EAST: nearest paid DC is in NC or OH
- US-EAST: nearest always-free DC is in SC or IA

### Oracle Cloud

Link: https://www.oracle.com/cloud/free/

30-Days Free:
- 30-day, $300 Free Trial for new accounts only

Always-Free:
- 2 AMD-based VMs: 0.25 vCPU and 1 GB RAM each;
- 4 Arm-based VMs: 24 GB RAM total, 3,000 vCPU hours and 18,000 GB hours per month;
- Storage:
  - 2 Block Volumes Storage, 200 GB total;
  - 10 GB Object Storage - Standard;
  - 10 GB Object Storage - Infrequent Access;
  - 10 GB Archive Storage;
  - 10TB of network egress;

### LINODE

No Free Tier, but $50 credit for 60 days
- Credit goes up to $100 for 60 days when using a YouTube influencer link

- VMs start from $5/month (for 1CPU/1GB RAM/SSD)
- US-EAST: Nearest DC is in Newark, NJ

### Digital Ocean

No Free Tier, but $100 credit for 60 days

- VMs start from $4/month (for 1CPU/512MB RAM/SSD)
- US-EAST: Nearest DC is in New York City, NY

## Cloud Storage Comparison:

### AWS

- Standard: $21/TB/month ($0.021/GB/month)
- $0.05+/GB for bandwidth

### Azure

- Standard: $17.40/TB/month ($0.017/GB/month)
- $0.04+/GB for bandwidth

### GCP

- Standard: $20.48/TB/month ($0.02/GB/month)
- $0.12/GB for bandwidth

### Backblaze

- URL: https://www.backblaze.com/b2/cloud-storage.html
- 3 regions (2 in U.S. and 1 in E.U.)
- $5/TB/month ($0.00488/GB/month): https://www.backblaze.com/b2/cloud-storage-pricing.html
- $0.01/GB bandwidth

### Wasabi

- URL: https://wasabi.com/cloud-storage-pricing
- $5.99/TB/mo
- Unlimited free egress
- Minimum storage policy requiring a minimum of 1TB of data stored
- Minimum storage duration policy that requires you to pay a minimum of 90 days storage
- Bandwidth fair use policy that doesn't allow more upload vs. download volume
- S3 compatible

### Storj

- URL: https://www.storj.io/pricing
- Storage Cost: $4/TB/month ($0.0039/GB/month)
- Bandwidth Cost: $7/TB ($0.0068/GB)
- 150GB for free
- 3 regions: US1, EU1, AP1
- smallest billing increment for a file is 64MB - not suitable for small files
- S3 compatible
- 16,000+ nodes in 99+ countries: https://storjnet.info/

### CloudFlare R2

- URL: https://www.cloudflare.com/products/r2/
- $15/month/TB ($0.015/GB/month)
- no egrees fees
- 10GB free tier
- S3 compatible

### Dropbox

### Google Drive

### OneDrive

### Linode

- $20/$TB/month

## Cloud Shell Comparison:

### Google Cloud Shell:
- based on Debian Linux, with 5GB persistent $HOME, 4 x vCPU, 16GB of RAM, SSD+HDD
- runs under K8s container with "best-effort" (low-class) QoS
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
- runs under an AWS ECS container and limits CPU to 1 CPU and RAM to 2GB
NB: limits: 20-30mins after logout resets VM (you get a new VM), max 12 hour session time, weekly usage limit (not sure?), 12hr max session, 1GB home-dir deleted >120 days (4 months) of inactivity
- sudo available - can install additional packages via yum
- web-only, no external IP address
- **web-url**: https://console.was.amazon.com/cloudshell/home?region=us-east-1

Documentation: https://docs.was.amazon.com/cloudshell/

### Azure Cloud Shell:
- based CBL Linux (based on Debian), with 5GB persistent 5GB $HOME, 2 x vCPU, 4GB RAM, HDD (no SSD)
- runs under K8s container with "burstable" (medium-class) QoS
- based on CBL - Common Base Linux (Microsoft Linux distribution), which is Debian like
- NB: no root access, no sudo, just your $HOME and /tmp, can not install additional system-wide packages/tools
      -> see suggestions: https://edyoung.github.io/blog/install_tools_locally/
      -> can also use tools such as `Junest' to be able to install packages
      -> can also use busybox: wget https://busybox.net/downloads/binaries/1.31.0-defconfig-multiarch-musl/busybox-x86_64
- NB: 20 mins timeout, 5GB home (paid), long-running sessions are terminated
- **web-url**: https://shell.azure.com

Documentation: https://docs.microsoft.com/en-us/azure/cloud-shell/overview

### OTHERS:
- http://www.pythonanywhere.com  <-- good spec (4x vCPU/16GB/Cascade Lake'19, NVMEe SSD), AWS, no root/no sudo, suited best for python
  - for $5-$6/month can be used with more features incl. SSH-in (ssh.pythonanywhere.com) and full internet access
  - PROS: fast AWS machine type: m5d.xlarge (4x vCPU/16GB/Cascade Lake'19/NVMEe SSD), easy web-accessibility, optional SSH access, Ubuntu
  - CONS: no-root/no-sudo, NFS mounted key directories, highly restricted build
- https://linuxcontainers.org/lxd/try-it/
  - root-based Ubuntu terminal, limited internet connectivity
- https://www.onworks.net/
  - can get Linux desktop access, incl. terminal, limited internet connectivity
- https://www.online-ide.com/  <-- can run basic shell commands, no outside internet access
  - VERY limited, not recommended for anything but testing
- https://www.webminal.org/terminal/  <-- basic shell, no outside internet access
  - VERY limited, not recommended for anything but testing

## Cloud Shell Pros+Cons

### GCP Cloud Shell:
+ SSH+web+app access
+ sudo
+ standard version of Linux (Ubuntu)
+ 4 vCPU + 16GB (incl. modern CPU)
+ `~/.customize_env`, most-flexible/customizable

- no SSD
- strict session limits
- "besteffort" (lowest) K8s QoS

### AWS CloudShell:
+ sudo
+ SSD

- older HW (slowest) & strict AWS ECS limits
- non-standard Linux (Amazon Linux 2)
- small Homedir @ 1GB
- seems slowest to start-up
- no app access (yet?)
- most restrictive container CPU+Mem limits

### Azure Cloud Shell:
+ recent HW
+ fast to start-up
+ "burstable" K8s QoS

- no sudo
- non-standard Linux (CBL Linux)
- web-only+app, no SSH
- charged for the 5GB Homedir
- no SSD
