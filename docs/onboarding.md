# Onboarding
For general GCP organization/quota/cloud-identity onboarding see https://github.com/GoogleCloudPlatform/pubsec-declarative-toolkit/wiki/Onboarding
- A new GCP day0 organization creation walkthrough is in https://github.com/GoogleCloudPlatform/pubsec-declarative-toolkit/issues/296
- see the types of workspace or cloud identity step for the new org - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/blob/main/z_2024_v020_pre_tef_v4/docs/google-cloud-onboarding.md
- the most relevant scenario is 3rd party domain and email account below
https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/blob/main/z_2024_v020_pre_tef_v4/docs/google-cloud-onboarding.md#onboarding-category-3b1-3rd-party-email-account---3rd-party-aws-route53-domain-validation---reuse-existing-billing-account
- Workspace account https://workspace.google.com/business/signup/welcome

# Options for Landing Zone Deployment
V20240425
## Deployment Options
As of 20240425 I recommend the following.  If you want to get the LZ up as-is - use the CB/CSR default option below.  If you need the ADO (Azure DevOps) version - this is currently the default deploy goal for the main branch and is actively being worked out but not tested yet.

## 20240504: Repo state: CB/CSR are the default for the main branch
The main branch is ready for Cloud Build / Cloud Source Repositories out of the box.  For ADO support this is in queue via https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/399 after a TEF upstream merge via https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/387

## 20240502: Repo state
The current main branch has a partial switch to local deployment in prep of ado.  There was a pr merged without readme adjustments and without the full retrofit towards ado support and local terraform support - as an addition not the current removal - see 399

To bring up CB/CSR for now - use the older clean branch
https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/tree/gh357-tef-v4-fork

With the addition of the 2nd/3rd PR before the disablement of CB.tf went in
- https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/pull/363
- https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/pull/369

This branch is essentially still a clean TEF copy with some readme, service, IAM changes before pulling out cloud build and csr.

## Issues general to the Landing Zone
- Work items:  https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/wiki/Work-Items
- see issue list
- - This PBMM repo - issues carried over from the TEF - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/376
- - TEF issues - curated list - https://github.com/terraform-google-modules/terraform-example-foundation/issues/1133#issuecomment-1980982638
- - TEF issues in queue search on mromascanu123 in https://github.com/terraform-google-modules/terraform-example-foundation/issues
- - TEF issues in queue search on obriensystems in https://github.com/terraform-google-modules/terraform-example-foundation/issues?q=is%3Aissue+is%3Aclosed
- - TEF issues in queue search on fmichaelobrien in https://github.com/terraform-google-modules/terraform-example-foundation/issues?q=is%3Aissue+is%3Aclosed
- Consult architecture docs reverse engineering and WIP in https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/wiki/Architecture
- full automation is pending - there are script fragments in the 6 readmes but care must be taken to mitigate any out of order execution
- periodic terraform timeouts - retry
- periodic API concurrent operations quota issues - retry after 30 min - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/wiki/DevOps#concurrent-operations-quota-exceeded-during-terraform-apply
- Some IAM permissions issues may still be existing - most are added
- the bootstrap project must have additional services enabled - see https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/wiki/DevOps#add-project-services and https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/pull/363/files
- Make sure to have over 50 - both project and billing quota
- Issues running terraform locally on windows machines because of symlinks
- for now (to avoid a statefile corruption between 0 and 1 stages) downgrade terraform 1.7.5 in cloud shell - per session to 1.3 via procedure https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/wiki/DevOps#terraform-downgrade-on-demand-per-cloud-shell-session
- LZ delete (terraform destroy + gcloud script deletes) are in progress but not working yet
- LZ Multi-tenancy as in 2+ LZs deployed per organization is also a WIP around org level collisions - the code is in main but needs to be fully verified. see https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/pull/385
## Cloud Build and CSR based Deployment
- working but note issues above
- use the following clean branch for cloud build
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/tree/gh357-tef-v4-fork
- - with changes in https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/pull/366
- - and add https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/pull/363
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/pull/369
- will deploy until 5-app-infra but the CB triggers are missing for this section - adding
## ADO based Deployment
- in progress in main via https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/399
- ADO dockerfile and pipeline work is currently interleaved in main as a WIP
- repo is being localized and pipelines are being added
- cb bootstrap module is commented out
## Feature Requests in queue
- a replacement for the transitivity VMs via Fortinet Fortigates and optionally GCP Firewall+/NGFW
-


# Example Landing Zone Deploy with Decisions
## Decide Workspace or Cloud Identity Super Admin account
## Decide cloud shell, local SDK or VM/AVD
## If not cloud shell - install SDK, GCP authenticate and set billing credentials on local shell/VM
## Clean GCP Organization with domain registration/validation
## 52+ Quota required for billing and projects quota
## Create LZ folder
## Create bootstrap project off folder
## Add service enablement to bootstrap project
## Add IAM roles to super admin account
## Clone base repo
## Doing 0-bootstrap
### Copy 0-bootstrap tfvars
### Verify GCP groups set or not set
- enterprise setup may have added them already
### Fill out tfvars
- orgid, billingid, create groups (2) flags, group emails
- region (this one is problematic as of 202404)
### Modify any hardcoded regions in the yamls
### Downgrade to Terraform 1.3.10 for now
### optionally skip validation - issue with main
### terraform init
### terraform plan
### terraform apply
### Triage any authentication timeout errors with exponential backoff and relogin
### Triage any IAM errors with IAM role additions - raise PR
### Triage any service errors with service enablements on bootstrap project - raise PR
### Triage any errors on tfvars configuration errors - rerun apply
### Triage any idempotent errors on existing service collisions on 2nd run - rename/orphan/delete - rerun apply
### Triage any authentication timeout errors with exponential backoff and relogin
### apply is complete - note terraform outputs



### Triage any groups creation errors

# Authentication
## New PubSec login
- 
![image](https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/assets/24765473/a22b9a6a-efde-4220-86d1-0c1777bcb3a9)
