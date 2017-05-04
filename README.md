# federation-users
List of some users of [kubernetes cluster federation](https://kubernetes.io/docs/concepts/cluster-administration/federation/)

Aim is:
* Help the development team understand how federation is being used most.
* Get answer to questions like "has anyone tried federation on \<cloud-provider\>" or "is anyone using federation in production".

This is by no means an exhaustive list. Just a sample of users.
Please feel free to send a PR to keep this updated.


# Managing multiple clusters in different AWS regions (Atlassian)
* Use case: HA mainly, being able to use clusters in lots of regions.
* Cloud provider: AWS
* Trying out/staging/production: staging/testing
* Setup details: Our eventual plan is to have lots of clusters (at least 9 in the US alone), managed by a federation per geo, (ie, one federation for all the US AWS regions), to enable our internal platform customers to deploy to all the regions and AWS AZs by talking to one API. That gets us single-pane-of-glass and HA.
* Contact details: nyoung @ atlassian.com email, @youngnick on twitter.

# Managing multiple clusters in different AWS regions (hp.com)
* Use case: manage multiple clusters in different regions
* Cloud provider: AWS
* Trying out/staging/production: staging/testing. Planning to move to production in June 2017.
* Setup details: Using Federation for managing AWS regions (us-east and us-west). Will be adding eu-frankfurt in fall. Some APJ region next year.
   Right now both clusters are almost identical. Will be adding more services later, and some will be on specific legal zones, so some regions only. Have the use case of multiple regions for HA, and multiple regions for policy compliance. Right now HA is the main use case.
* Auth across clusters: Share the same identities, on stage and prod, only the pipelines (Jenkins2) can access. Dev is open to most developers.
* Contact details: galo@hp.com, eduardo@hp.com.

# Hybrid setup with AWS, On prem, Azure and Cloudstack
* Use case: Hybrid k8s, Multi Tenancy, treating clusters as cattle not pets (replace clusters, don't upgrade them), abstract from IaaS providers without changing application landscape.
* Cloud provider: AWS, On prem, Azure, Cloudstack
* Trying out/staging/production: staging/testing
* Setup details: Working on PoC use cases for multi cloud, multi region setups. Using federation as a multi tenancy endpoint for clusters using OPA or RBAC to determine the correct clusters to use. Using federation for dynamic public DNS gLB for clusters that are on prem but want to use Public Cloud services.
* Contact details: @SethKarlo on twitter and Slack, email address is arepton @ schubergphilis.com

# Hybrid setup with GCP and On prem
* Use case: Hybrid/cloudbursting
* Cloud provider: GCP, On prem
* Trying out/staging/production: Trying out
* More details: Running federation control plane on Google cloud and clusters on-prem. Trying to setup a full on-prem. More details: https://github.com/henriquetruta/hybrid-k8s-federation/
* Contact details: htruta @ slack
