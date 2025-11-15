
 create mode 100644 terraform/.terraform.lock.hcl
 create mode 100644 terraform/.terraform/providers/registry.terraform.io/hashicorp/aws/3.76.1/windows_amd64/terraform-provider-aws_v3.76.1_x5.exe    
 create mode 100644 terraform/0-auth.tf
 create mode 100644 terraform/1-vpc.tf
 create mode 100644 terraform/10-autoscalinggroup.tf
 create mode 100644 terraform/11-route53.tf
 create mode 100644 terraform/2-subnets.tf
 create mode 100644 terraform/3-igw.tf
 create mode 100644 terraform/4-nat.tf
 create mode 100644 terraform/5-route.tf
 create mode 100644 terraform/6-sg01-all.tf
 create mode 100644 terraform/7-launchtemplate.tf
 create mode 100644 terraform/8-targetgroup.tf
 create mode 100644 terraform/9-loadbalancer.tf
 create mode 100644 terraform/terraform.tfstate
 create mode 100644 terraform/terraform.tfstate.backup
 create mode 100644 terraform/terraform.tfvars
 create mode 100644 terraform/variables-route53.tf

tawan@TP MINGW64 ~/ASG-PrettySite-Route53 (main)
$ cd ~/ASG-PrettySite-Route53

tawan@TP MINGW64 ~/ASG-PrettySite-Route53 (main)
$ ls
index.html  style.css  terraform/

tawan@TP MINGW64 ~/ASG-PrettySite-Route53 (main)
$ git add .

tawan@TP MINGW64 ~/ASG-PrettySite-Route53 (main)
$ git commit -m "Add Terraform ASG, ALB, Route53 infrastructure code"
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

tawan@TP MINGW64 ~/ASG-PrettySite-Route53 (main)
$ git status
git push origin main
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
Enumerating objects: 29, done.
Counting objects: 100% (29/29), done.
Delta compression using up to 12 threads
Compressing objects: 100% (22/22), done.
Writing objects: 100% (28/28), 54.43 MiB | 2.09 MiB/s, done.
Total 28 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), done.
remote: error: Trace: 90779489bb9fbdc53ddae52eea2d9c189cda2d81265771eac399885fe1945132
remote: error: See https://gh.io/lfs for more information.
remote: error: File terraform/.terraform/providers/registry.terraform.io/hashicorp/aws/3.76.1/windows_amd64/terraform-provider-aws_v3.76.1_x5.exe is 247.48 MB; this exceeds GitHub's file size limit of 100.00 MB
remote: error: GH001: Large files detected. You may want to try Git Large File Storage - https://git-lfs.github.com.
To https://github.com/tawanmaurice/ASG-PrettySite-Route53.git
 ! [remote rejected] main -> main (pre-receive hook declined)
error: failed to push some refs to 'https://github.com/tawanmaurice/ASG-PrettySite-Route53.git'

tawan@TP MINGW64 ~/ASG-PrettySite-Route53 (main)
$
