# ep12-uptime-with-cert-manager
 pop22 usercase

Prepare: 
- DNS map host.domain (A record) to Layer4 loadbalance
    - 202.28.230.84
    - 203.158.118.77
- if run staging can use hostname on this domain
    - [hostname].cb9e764d.nip.io
    - [hostname].ca1ce654.nip.io
    - [hostname].ca1cfd03.nip.io
- Edit file (stepx...) change namespace, hostname with your information of cluster

- Deployment step:
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
