# DevOps Procedures

## Source
- Cloud Foundation Toolkit source for terraform-google-modules - https://github.com/GoogleCloudPlatform/cloud-foundation-toolkit/blob/master/infra/terraform/test-org/org/locals.tf#L147

## TEF Install Procedure
- General guide in https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/wiki/Onboarding#options-for-landing-zone-deployment
- follow end to end Cloud Build / CSR based procedure from 0 to 5 in https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/360
### Existing Organization

### Cloud Shell
### Local Windows
- see https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/wiki/DevOps#authenticate-a-local-cloud-shell
- TODO - verify sh on windows working with ming64 https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/429
#### Install Gcloud SDK
- https://cloud.google.com/sdk/docs/install

```
C:\wse_github\GoogleCloudPlatform\p6gen1>gcloud init
gcloud components update
``` 
![image](https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/assets/24765473/26f1f66f-9639-4781-9a14-21731151d9ac)

#### Load puttygen, certificate, clone repo
- https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

```
git clone git@github.com:GoogleCloudPlatform/pbmm-on-gcp-onboarding.git
```
### Local OSX

### Create folder off org
![image](https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/assets/24765473/dacf13e1-c5e3-4b1d-bb37-0872a0fc68d8)

after about 2 min note the folder id ie: "878436685331"
### Create bootstrap project off folder
![image](https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/assets/24765473/b5b5f77f-5834-49b6-b121-d7946f18b31c)





### Add project services
```

gcloud config set project tef-oldev2

exiting services
gcloud services list
NAME                                TITLE
analyticshub.googleapis.com         Analytics Hub API
bigquery.googleapis.com             BigQuery API
bigqueryconnection.googleapis.com   BigQuery Connection API
bigquerydatapolicy.googleapis.com   BigQuery Data Policy API
bigquerymigration.googleapis.com    BigQuery Migration API
bigqueryreservation.googleapis.com  BigQuery Reservation API
bigquerystorage.googleapis.com      BigQuery Storage API
cloudapis.googleapis.com            Google Cloud APIs
cloudtrace.googleapis.com           Cloud Trace API
dataform.googleapis.com             Dataform API
dataplex.googleapis.com             Cloud Dataplex API
datastore.googleapis.com            Cloud Datastore API
logging.googleapis.com              Cloud Logging API
monitoring.googleapis.com           Cloud Monitoring API
servicemanagement.googleapis.com    Service Management API
serviceusage.googleapis.com         Service Usage API
sql-component.googleapis.com        Cloud SQL
storage-api.googleapis.com          Google Cloud Storage JSON API
storage-component.googleapis.com    Cloud Storage
storage.googleapis.com              Cloud Storage API

Add the following
gcloud services enable cloudresourcemanager.googleapis.com
gcloud services enable cloudbilling.googleapis.com
gcloud services enable iam.googleapis.com
gcloud services enable cloudkms.googleapis.com
gcloud services enable servicenetworking.googleapis.com
gcloud services enable cloudidentity.googleapis.com
gcloud services enable cloudbuild.googleapis.com

```

### Check IAM roles on super admin

### Terraform downgrade to 1.3.10
- https://releases.hashicorp.com/terraform/1.3.10
```
terraform --version
Terraform v1.3.10
on windows_amd64

Your version of Terraform is out of date! The latest version
is 1.8.2. You can update by downloading from https://www.terraform.io/downloads.html
```
### Terraform downgrade to 1.6.6
From 1.7.5 to 1.6.6
https://releases.hashicorp.com/terraform/1.6.6/
```
michael@cloudshell:~/tef-oldev/github/pbmm-on-gcp-onboarding/0-bootstrap (tef-oldev)$ cd ~/
michael@cloudshell:~ (tef-oldev)$ wget https://releases.hashicorp.com/terraform/1.6.6/terraform_1.6.6_linux_amd64.zip
--2024-04-11 01:09:45--  https://releases.hashicorp.com/terraform/1.6.6/terraform_1.6.6_linux_amd64.zip
Resolving releases.hashicorp.com (releases.hashicorp.com)... 13.35.116.98, 13.35.116.16, 13.35.116.54, ...
Connecting to releases.hashicorp.com (releases.hashicorp.com)|13.35.116.98|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 24976120 (24M) [application/zip]
Saving to: ‘terraform_1.6.6_linux_amd64.zip’

terraform_1.6.6_linux_amd64.zip     100%[===================================================================>]  23.82M  43.5MB/s    in 0.5s    

2024-04-11 01:09:45 (43.5 MB/s) - ‘terraform_1.6.6_linux_amd64.zip’ saved [24976120/24976120]

michael@cloudshell:~ (tef-oldev)$ unzip terraform_1.6.6_linux_amd64.zip 
Archive:  terraform_1.6.6_linux_amd64.zip
  inflating: terraform 
michael@cloudshell:~ (tef-oldev)$ which terraform
/usr/bin/terraform
michael@cloudshell:~ (tef-oldev)$ sudo cp terraform /usr/bin
michael@cloudshell:~ (tef-oldev)$ sudo chmod 777 /usr/bin/terraform 
michael@cloudshell:~ (tef-oldev)$ terraform --version
Terraform v1.6.6
on linux_amd64
Your version of Terraform is out of date! The latest version
is 1.8.0. You can update by downloading from https://www.terraform.io/downloads.html   
```

### Terraform Downgrade on demand per cloud shell session
```
michael@cloudshell:~/tef-olxyz/github/gcp-projects (tef-olxyz)$ terraform --version
Terraform v1.7.5
on linux_amd64

Your version of Terraform is out of date! The latest version
is 1.8.0. You can update by downloading from https://www.terraform.io/downloads.html
michael@cloudshell:~/tef-olxyz/github/gcp-projects (tef-olxyz)$ ls ../../
github  README.md  terraform  terraform_1.3.10_linux_amd64.zip
michael@cloudshell:~/tef-olxyz/github/gcp-projects (tef-olxyz)$ 
michael@cloudshell:~/tef-olxyz/github/gcp-projects (tef-olxyz)$ which terraform
/usr/bin/terraform
michael@cloudshell:~/tef-olxyz/github/gcp-projects (tef-olxyz)$ sudo cp ../../terraform /usr/bin/terraform 
michael@cloudshell:~/tef-olxyz/github/gcp-projects (tef-olxyz)$ terraform --version
Terraform v1.3.10
on linux_amd64

Your version of Terraform is out of date! The latest version
is 1.8.0. You can update by downloading from https://www.terraform.io/downloads.html
```


## No terraform output - check statefile or proper directory
```
michael@cloudshell:~/tef-olxyz/github/gcp-networks (tef-olxyz)$ export network_step_sa=$(terraform output -raw networks_step_terraform_service_account_email)
michael@cloudshell:~/tef-olxyz/github/gcp-networks (tef-olxyz)$ echo "network step service account = ${network_step_sa}"
network step service account = ╷
│ Warning: No outputs found
│ 
│ The state file either has no outputs defined, or all the defined outputs are empty. Please define an output in your configuration with the `output` keyword and run `terraform
│ refresh` for it to become available. If you are using interpolation, please verify the interpolated value is not empty. You can use the `terraform console` command to assist.
╵
michael@cloudshell:~/tef-olxyz/github/gcp-networks (tef-olxyz)$ cd ../gcp-bootstrap/
michael@cloudshell:~/tef-olxyz/github/gcp-bootstrap (tef-olxyz)$ cd ../pbmm-on-gcp-onboarding/
michael@cloudshell:~/tef-olxyz/github/pbmm-on-gcp-onboarding (tef-olxyz)$ cd 0-bootstrap/
michael@cloudshell:~/tef-olxyz/github/pbmm-on-gcp-onboarding/0-bootstrap (tef-olxyz)$ export network_step_sa=$(terraform output -raw networks_step_terraform_service_account_email)michael@cloudshell:~/tef-olxyz/github/pbmm-on-gcp-onboarding/0-bootstrap (tef-olxyz)$ echo "network step service account = ${network_step_sa}"
network step service account = sa-terraform-net@prj-b-seed-8919.iam.gserviceaccount.com
michael@cloudshell:~/tef-olxyz/github/pbmm-on-gcp-onboarding/0-bootstrap (tef-olxyz)$ terraform output
bootstrap_step_terraform_service_account_email = "sa-terraform-bootstrap@prj-b-seed-8919.iam.gserviceaccount.com"
cloud_build_peered_network_id = "projects/prj-b-cicd-82vv/global/networks/vpc-b-cbpools"
cloud_build_private_worker_pool_id = "projects/prj-b-cicd-82vv/locations/us-central1/workerPools/private-pool-yqvb"
cloud_build_worker_peered_ip_range = "192.168.0.0/24"
```

## Build and Repositories
### Cloud Build and Cloud Source Repositories
### Azure DevOps
see work in https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/399
#### ADO Setup
- Get a Microsoft account
- Get an Azure account
- Get an ADO account
- - https://learn.microsoft.com/en-us/azure/devops/organizations/billing/overview?view=azure-devops

#### ADO SSH key
- https://learn.microsoft.com/en-us/azure/devops/repos/git/use-ssh-keys-to-authenticate?view=azure-devops

```
# on mac
ssh-keygen -t rsa -b 4096 -C "mic..yz" 
michaelobrien@mbp7 pbmm-on-gcp-onboarding % cp ado_olxyz.* ~/keys 
michaelobrien@mbp7 pbmm-on-gcp-onboarding % cp ado_olxyz ~/keys       
michaelobrien@mbp7 pbmm-on-gcp-onboarding % chmod 400 ~/keys/ado_olxyz
michaelobrien@mbp7 pbmm-on-gcp-onboarding % ssh-add ~/keys/ado_olxyz
Identity added: /Users/michaelobrien/keys/ado_olxyz (michael@obrienlabs.xyz)
michaelobrien@mbp7 pbmm-on-gcp-onboarding % cat ~/keys/ado_olxyz.pub 

paste to https://dev.azure.com/obrienlabsxyz/_usersSettings/keys
```
<img width="1629" alt="Screenshot 2024-05-27 at 12 14 08" src="https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/assets/24765473/93a35fd1-f4b6-475c-899a-2db1f47044a7">


## Upstream Repository Sync
- https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/387

## github (upstream) - to ado repo

```
michaelobrien@mbp7 pbmm-on-gcp-onboarding % git remote add upstream https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding.git 
michaelobrien@mbp7 pbmm-on-gcp-onboarding % git fetch upstream
remote: Enumerating objects: 8, done.
remote: Counting objects: 100% (8/8), done.
remote: Compressing objects: 100% (8/8), done.
remote: Total 8 (delta 2), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (8/8), 7.72 KiB | 878.00 KiB/s, done.
From https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding
 * [new branch]      243-tef-retrofit                                               -> upstream/243-tef-retrofit
...
michaelobrien@mbp7 pbmm-on-gcp-onboarding % git merge upstream/main main  
Already up to date.
```
expected - as we just cloned the repo into ADO - however pull in some new changes on the upstream branch
```

michaelobrien@mbp7 pbmm-on-gcp-onboarding % git checkout --track origin/gh399-ado
branch 'gh399-ado' set up to track 'origin/gh399-ado'.
Switched to a new branch 'gh399-ado'


michaelobrien@mbp7 pbmm-on-gcp-onboarding % git remote -v                                                                            
origin	https://obrienlabsxyz@dev.azure.com/obrienlabsxyz/pbmm-on-gcp-onboarding/_git/pbmm-on-gcp-onboarding (fetch)
origin	https://obrienlabsxyz@dev.azure.com/obrienlabsxyz/pbmm-on-gcp-onboarding/_git/pbmm-on-gcp-onboarding (push)
upstream	https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding.git (fetch)
upstream	https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding.git (push)
michaelobrien@mbp7 pbmm-on-gcp-onboarding % vi 0-bootstrap/terraform.example.tfvars                                                  
michaelobrien@mbp7 pbmm-on-gcp-onboarding % git merge upstream/gh399-ado gh399-ado                                                                        
Merge made by the 'ort' strategy.
 0-bootstrap/README-Azure-DevOps.md   | 115 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++-----
 0-bootstrap/README.md                |  19 +++++++++++++++++++
 0-bootstrap/terraform.example.tfvars |  18 +++++++++++++++++-
 0-bootstrap/variables.tf             |   7 +++++++
 0-bootstrap/versions.tf              |   7 +++++++
 5 files changed, 160 insertions(+), 6 deletions(-)
michaelobrien@mbp7 pbmm-on-gcp-onboarding % git status
On branch gh399-ado
Your branch is ahead of 'origin/gh399-ado' by 14 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
michaelobrien@mbp7 pbmm-on-gcp-onboarding % git commit -m "#399 - github to ado upstream merge"
On branch gh399-ado
Your branch is ahead of 'origin/gh399-ado' by 14 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
michaelobrien@mbp7 pbmm-on-gcp-onboarding % git push origin gh399-ado                                                                                     
Enumerating objects: 74, done.
Counting objects: 100% (68/68), done.
Delta compression using up to 10 threads
Compressing objects: 100% (54/54), done.
Writing objects: 100% (54/54), 14.85 KiB | 14.85 MiB/s, done.
Total 54 (delta 40), reused 0 (delta 0), pack-reused 0
remote: Analyzing objects... (54/54) (10 ms)
remote: Validating commits... (14/14) done (1 ms)
remote: Storing packfile... done (89 ms)
remote: Storing index... done (63 ms)
To https://dev.azure.com/obrienlabsxyz/pbmm-on-gcp-onboarding/_git/pbmm-on-gcp-onboarding
   bb6d4e0..bc6bc4c  gh399-ado -> gh399-ado


```
<img width="1463" alt="Screenshot 2024-04-29 at 12 04 05" src="https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/assets/24765473/446984cd-3b24-478c-878f-90bc3c9505e7">



## FAQ

### Authenticate a Local cloud shell
#### Initial state = service account impersonation for different org
- Service Account Impersonation between orgs is detailed in https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/449

On mac
```
michaelobrien@mbp7 pbmm-on-gcp-onboarding % gcloud config list
[auth]
impersonate_service_account = bigquery-ol-sa@bigquery-ol.iam.gserviceaccount.com
[compute]
region = us-central1
zone = us-central1-a
[core]
account = michael@obrienlabs.xyz
disable_usage_reporting = False
project = bigquery-ol

Your active configuration is: [obrienlabs-dev]

Updates are available for some Google Cloud CLI components.  To install them,
please run:
  $ gcloud components update
```
#### Final state = direct super admin access for target org
- https://cloud.google.com/docs/authentication/gcloud#local
```
michaelobrien@mbp7 pbmm-on-gcp-onboarding % gcloud init
Welcome! This command will take you through the configuration of gcloud.

Settings from your current configuration [obrienlabs-dev] are:
auth:
  impersonate_service_account: bigquery-ol-sa@bigquery-ol.iam.gserviceaccount.com
compute:
  region: us-central1
  zone: us-central1-a
core:
  account: michael@obrienlabs.xyz
  disable_usage_reporting: 'False'
  project: bigquery-ol

Pick configuration to use:
 [1] Re-initialize this configuration [obrienlabs-dev] with new settings 
 [2] Create a new configuration
 [3] Switch to and re-initialize existing configuration: [cloud-code]
 [4] Switch to and re-initialize existing configuration: [default]
 [5] Switch to and re-initialize existing configuration: [michael-clouddevops-dev]
Please enter your numeric choice:  2

Enter configuration name. Names start with a lower case letter and contain only lower case letters a-z, digits 0-9, and hyphens '-':  olapp
Your current configuration has been set to: [olapp]

You can skip diagnostics next time by using the following flag:
  gcloud init --skip-diagnostics

Network diagnostic detects and fixes local network connection issues.
Checking network connection...done.                                                                                                                                              
Reachability Check passed.
Network diagnostic passed (1/1 checks passed).

Choose the account you would like to use to perform operations for this configuration:
 [1] michael@clouddevops.dev
 [2] michael@containerized.org
 [3] michael@obrienlabs.dev
 [4] michael@obrienlabs.xyz
 [5] root@kcc.landing.systems
 [6] Log in with a new account
Please enter your numeric choice:  6

Your browser has been opened to visit:

    https://accounts.google.com/o/oauth2/auth?response_type=code&client_id=32555940559.apps.googleusercontent.com&redirect_uri=http%3A%2F%2Flocalhost%3A8085%2F&scope=openid+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fuserinfo.email+htt..._method=S256

You are logged in as: [michael@obrienlabs.app].

Pick cloud project to use: 
 [1] fortigate-terraform-olapp
 [2] gcloud-ola
 [3] kcc-olapp
 [4] prj-b-cicd-wm4z
 [5] prj-b-seed-31ca
 [6] tef-olapp
 [7] Enter a project ID
 [8] Create a new project
Please enter numeric choice or text value (must exactly match list item):  tef-olapp

Your current project has been set to: [tef-olapp].

Not setting default zone/region (this feature makes it easier to use
[gcloud compute] by setting an appropriate default value for the
--zone and --region flag).
See https://cloud.google.com/compute/docs/gcloud-compute section on how to set
default compute region and zone manually. If you would like [gcloud init] to be
able to do this for you the next time you run it, make sure the
Compute Engine API is enabled for your project on the
https://console.developers.google.com/apis page.

Your Google Cloud SDK is configured and ready to use!

* Commands that require authentication will use michael@obrienlabs.app by default
* Commands will reference project `tef-olapp` by default
Run `gcloud help config` to learn how to change individual settings

This gcloud configuration is called [olapp]. You can create additional configurations if you work with multiple accounts and/or projects.
Run `gcloud topic configurations` to learn more.

Some things to try next:

* Run `gcloud --help` to see the Cloud Platform services you can interact with. And run `gcloud help COMMAND` to get help on any gcloud command.
* Run `gcloud topic --help` to learn about advanced features of the SDK like arg files and output formatting
* Run `gcloud cheat-sheet` to see a roster of go-to `gcloud` commands.

michaelobrien@mbp7 pbmm-on-gcp-onboarding % gcloud config set project tef-olapp
WARNING: Your active project does not match the quota project in your local Application Default Credentials file. This might result in unexpected quota issues.

To update your Application Default Credentials quota project, use the `gcloud auth application-default set-quota-project` command.
Updated property [core/project].

```

#### Fix ADC for local user credentials
- https://cloud.google.com/docs/authentication/provide-credentials-adc#local-user-cred
```
michaelobrien@mbp7 pbmm-on-gcp-onboarding % gcloud auth application-default set-quota-project tef-olapp
ERROR: (gcloud.auth.application-default.set-quota-project) The application default credentials are not user credentials, quota project cannot be added.
```

<img width="1489" alt="Screenshot 2024-04-30 at 11 06 51" src="https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/assets/24765473/e6635078-8c71-4b46-a6c8-005042541feb">

```
michaelobrien@mbp7 pbmm-on-gcp-onboarding % gcloud auth application-default login
Your browser has been opened to visit:

    https://accounts.google.com/o/oauth2/auth?response_type=code&client_id=764086051850-6qr4p6gpi6hn506pt8ejuq83d...hod=S256

Credentials saved to file: [/Users/michaelobrien/.config/gcloud/application_default_credentials.json]

These credentials will be used by any library that requests Application Default Credentials (ADC).

Quota project "tef-olapp" was added to ADC which can be used by Google client libraries for billing and quota. Note that some services may still bill the project owning the resource.

```

<img width="1494" alt="Screenshot 2024-04-30 at 11 12 47" src="https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/assets/24765473/3e599693-5c52-4b21-b206-2740ec4c1298">

```
we are good now
ichaelobrien@mbp7 pbmm-on-gcp-onboarding % gcloud config set project tef-olapp                        
Updated property [core/project].
```


### Concurrent operations quota exceeded during terraform apply
In this case in 4-projects production apply

see https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/391
retry fixes the API quota CONCURRENT_OPERATIONS_QUOTA_EXCEEDED issue - wait 60 min - now we see all shared VPCs for business units
<img width="1443" alt="Screenshot 2024-04-16 at 16 23 01" src="https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/assets/24765473/9f9ab292-cec4-4ccc-9c8e-ad01073489b3">

<img width="1072" alt="Screenshot 2024-04-16 at 16 20 57" src="https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/assets/24765473/ed89124f-bc2d-4f1e-bc90-6b837e30c148">

## Running in an ubuntu container
```
docker run -it --rm --name ubuntu ubuntu:18.04 /bin/bash
with persistence

C:\wse_github\GoogleCloudPlatform\p6gen1\pbmm-on-gcp-onboarding\0-bootstrap>docker run -it --name ubuntu -v .:/bootstrap ubuntu
:18.04 /bin/bash
root@f65e48cd0e9c:/# ls boot
root@f65e48cd0e9c:/# ls bootstrap
Dockerfile                 backend.tf.local    modules                     terraform.exe
README-GitHub.md           cb.tf               onprem.md                   terraform.tfvars
README-GitLab.md           files               outputs.tf                  terraform_cloud.tf.example
README-Jenkins.md          github.tf.example   outputs.tf.local            variables.tf
README-Terraform-Cloud.md  gitlab.tf.example   provider.tf                 versions.tf
README.md                  groups.tf           sa.tf
backend.tf.cloud.example   jenkins.tf.example  scripts
backend.tf.example         main.tf             terraform-local.tf.example

```

## Cloud Shell Drive Saturation
```
Welcome to Cloud Shell! Type "help" to get started.
To set your Cloud Platform project in this session use “gcloud config set project [PROJECT_ID]”
Your home disk usage is at 99%.
You can find suggestions to clear space at https://cloud.google.com/shell/docs/quotas-limits#clearing_disk_space.
michael@cloudshell:~$ 

michael@cloudshell:~$ df
Filesystem                        1K-blocks      Used Available Use% Mounted on
overlay                           119475748 104165480  15293884  88% /
tmpfs                                 65536         0     65536   0% /dev
/dev/sda1                         119475748 104165480  15293884  88% /root
/dev/disk/by-id/google-home-part1   5018272   4523664    216132  96% /home
/dev/root                           2019696   1214236    805460  61% /usr/lib/modules
```
## Simulation
### Simulate GKE zone Failures
- https://cloud.google.com/kubernetes-engine/docs/tutorials/simulate-zone-failure
