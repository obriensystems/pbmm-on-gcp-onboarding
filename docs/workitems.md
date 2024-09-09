# TEF V5 tracking
https://github.com/terraform-google-modules/terraform-example-foundation/labels/v5.0
# Engagement
- PR part 1 in PBMM
- PR part 2 upsource to TEF part 1

Tracking issue is [388](https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/388) and [378](https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/376)

## PRs merged to the terraform-example-foundation upstream repo
- 20240426 bootstrap project has additional service enablements and roles now (for new orgs) https://github.com/terraform-google-modules/terraform-example-foundation/pull/1175 (same fix as https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/pull/363 )

## PRs in queue for the terraform-example-foundation upstream repo
- region hardcoding https://github.com/terraform-google-modules/terraform-example-foundation/pull/1181 for https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/405
- 20240512: https://github.com/terraform-google-modules/terraform-example-foundation/pull/1230
- 20240512: https://github.com/terraform-google-modules/terraform-example-foundation/pull/1232

## Full Run through the TEF
- via TEF - https://github.com/terraform-google-modules/terraform-example-foundation/issues/1133
- via PBMM copy - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/360
- via PBMM copy - main retrofit https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/421

## Work Items - In priority
Review original list in 
https://github.com/terraform-google-modules/terraform-example-foundation/issues/1133
https://github.com/terraform-google-modules/terraform-example-foundation/issues/1183

see ongoing list of so far minor issues we can move on from 
### Google Raised Issues
- PR navigation https://github.com/terraform-google-modules/terraform-example-foundation/issues/1179
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1135
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1136
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1137
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1138
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1139
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1140
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1141
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1142
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1143
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1144
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1145
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1146
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1147

20240312
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1149
- upstream rebase and retest with changes since 20240306 including
- https://github.com/terraform-google-modules/terraform-example-foundation/pull/1148/files
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1150
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1151
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1161
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1173
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1176
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1177
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1178

### Customer Raised Issues
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1166
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1167
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1168
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1169
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1170
- https://github.com/terraform-google-modules/terraform-example-foundation/issues/1172


### 20240508
- DI wiki https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/wiki/Design-Issues
- Issue tracking https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/376 and https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/388 

#### Done
- hardcoding removal
- - backport PR via https://github.com/terraform-google-modules/terraform-example-foundation/issues/1226
- parameterization via single config file
- - PR pending - related to https://github.com/terraform-google-modules/terraform-example-foundation/issues/1225
- local terraform running
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/pull/384
- - keep CB/CSR option https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/pull/423
- multi-tenant LZ (multi folder)
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/pull/385
- PBR script only example
- -

#### In progress
- review https://github.com/terraform-google-modules/terraform-example-foundation/issues/1167#issuecomment-2109200432
- example for example log-export 7.8 to 8.0

https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/pull/435/files#diff-5e4a99cddb50050455194466ec2ed0f1b0e924d90cd91d65c999ab4da57a8664L86
- Eliminate Hardcoding
- - https://github.com/terraform-google-modules/terraform-example-foundation/issues/1226
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/pull/393

- Automation
- - https://github.com/terraform-google-modules/terraform-example-foundation/issues/1225
- 3-n-h-a-s architecture adjustment
- - 
- keeping CB/CSR option along with new local TF and ADO options - currently switched via commenting but needs automation
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/421
- ADO - manual repos for now with optional pipeline trigger, terraform image is hardcoded for now - 
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/399
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/pull/408
- ADO - pipelines past 0-bootstrap - fully automated including dry-run - like or similar to CB https://console.cloud.google.com/cloud-build/builds;region=us-central1?referrer=search&project=prj-b-cicd-82vv&supportedpurview=project
- Windows support
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/429
#### Not started yet - what fits in Phase 1 delivery
- Fortigate integration - removal of existing transitive NVA's
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/389
- PBR Terraform integration of script example
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/373
- shared VPC subnet sharing at the individual level with services projects
- - 
- NGFW connectivity via terraform (later)
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/396

#### Not started yet - what is moved to Phase 2 delivery
- 


### 20240415
- Rename repo to terraform-google-pubsec-foundation - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/397 
- PBR routing - if via Terraform - we need a Teraform 1.6.later upgrade on the CB (DockerFile upgrade) - not required for local TF
https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/blob/main/0-bootstrap/Dockerfile#L18
```
ARG TERRAFORM_VERSION=1.3.0
```
- PBR routing - if via sh - no TF 1.3 upgrade
- https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/373

- localization(no cloud build - run TF locally) - done
- localization(terraform registry - version snapshots) - deferred - in progress via py script
- Hardcoding - Marian
- - 
- ADO Integration, (cloud shell testing as well) - Michael / Youssef
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/399
- - https://hub.docker.com/r/obrienlabs/terraform-example-foundation-ado/tags
- - for https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/409
- prep VPCs for Fortigates
- Fortigate Overlay on 3-shared-network-hub-and-spoke VPC (replace transitive NVA - shared
- - see https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/389
- - see https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/345
- - https://github.com/40net-cloud/fortinet-gcp-solutions/tree/master/FortiGate
- - https://github.com/fortinet/fortigate-tutorial-gcp/tree/main/terraform

- Google NGFW / Firewall+ (cloud native option to the Fortigate NGFW)
- - can be a direct copy/overlay on 3-networks-hub-and-spoke or a pluggable architecture where we can use any of the 3 - transitive VMs, Fortigates or GCP NFGW
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/396
- Architecture reverse engineering - shared
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/wiki/Architecture
- Automation/documentation - shared
- - Delete all or part of the LZ - repeated developer workflow - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/390
- French Documentation - either on-the-fly paired EN/FR or on demand - TBD
- ConOps - Concept of Operations document
- PBMM security review/evidence
- Port over org policies from KCC LZ V2 (check sec controls mappings) - review list
- - https://github.com/GoogleCloudPlatform/pubsec-declarative-toolkit/tree/main/solutions/core-landing-zone/org/org-policies
- - https://github.com/GoogleCloudPlatform/pubsec-declarative-toolkit/blob/main/solutions/core-landing-zone/org/org-policies/compute-restrict-vpc-peering.yaml#L36C1-L36C37 
- Recurrent downstream sync from the TEF - pulling in changes as required via diff
- - https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding/issues/387
- - see fork for reference https://github.com/CloudLandingZone/terraform-example-foundation/compare/master...terraform-google-modules%3Aterraform-example-foundation%3Amaster

## To Triage
- 1 - Multi-tenant is alluded to - half the changes to allow folder/per-dev-deploy are already done
- 2 - Functional tests for each component - will need to add golang testing modules for fortigates
- 3 - Validation: performance and load testing - we don’t really have a framework for integration (full LZ) load balancing but can test this easily with a canary workload in one of the BU projects off 4-projects
