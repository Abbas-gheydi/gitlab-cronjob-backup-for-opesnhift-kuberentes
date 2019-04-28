backup from gitlab hosted on openshift or kuberentes .  

first of all:   
my default path for google drive binary is:
/gdrive-backup/gdrive/

my gitlab deployment has lable of deploymentconfig=gitlab-ce

you can change these valuse in yaml files.



first create a service account in gitlab project (namespace) , this service account should have right permission to execute commands inside pods.

in openshift: oc create sa 4kubectl -n gitlab .  
in kubernetes: kubectl create sa 4kubectl .  

then set edit permission for this account .  
oadm policy add-role-to-user edit 4kubectl .  

oc create -f git-backup-to-local.yaml -n gitlab .  


to create a copy for local backup to google drive add this cronjob .  


oc create -f git-backup-to-gdrive.yaml -n gitlab .  

and follow thist git repo .   

https://github.com/Syonet/gitlab-backup-uploader
