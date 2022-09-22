# ep12-uptime-with-cert-manager
 Cluster "master"

Prepare: 
- DNS map host.domain (A record) to Layer4 loadbalance
    - 202.28.253.3
    - 203.158.118.77
- if run staging can use hostname on this domain
    - [hostname].ca1cfd03.nip.io

- Deployment step (now):
    - cp v2/MASTER-step1-ns.yml step1-ns.yml
    - cp v2/MASTER-step2-app.yml step2-app.yml
    - Find and replace (ste1-ns.yml, step2-app.yml)
        - APPNAME = [application name]
        - PRJECTID = [id from rancher web ui]
        - MYEMAIL = [email]  
        - CERTSTATE = [staging/prod]
    
    - example for MAC zsh 
        - sed -i '' 's/APPNAME/otj101/g' step1-ns.yml
        - sed -i '' 's/PROJECTID/c-m-7l8v45x2:p-z5t58/' step1-ns.yml
        - sed -i '' 's/APPNAME/otj101/' step2-app.yml
        - sed -i '' 's/MYEMAIL/ip@en.rmutt.ac.th/' step2-app.yml
        - sed -i '' 's/CERTSTATE/staging/' step2-app.yml
    
    - kubectl create -f step1-ns.yml
    - kubectl apply -f step2-app.yml    


- Deployment step for v1 (old) :
    - Edit file (stepx...) change namespace, hostname with your information of cluster
    - kubectl create -f step1-ns.yml
    - kubectl apply -f step2-cert-manager.yml
    - kubectl apply -f step3-uptime-app.yml
    - kubectl apply -f step4-ingress-prod.yml

Remark:
- issue-prod-cert.yml and issue-stag-cert.yml is template.
https://cert-manager.io/docs/
- uptime kuma
https://github.com/louislam/uptime-kuma



# อ่านเล่นๆ
- https://dev.to/freakynit/kubernetes-handnotes-2bm9
- https://kube.academy/courses
