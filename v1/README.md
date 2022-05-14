Prepare: 
- DNS map host.domain (A record) to Layer4 loadbalance
    - 202.28.230.84
    - 203.158.118.77
- if run staging can use hostname on this domain
    - [hostname].cb9e764d.nip.io
    - [hostname].ca1ce654.nip.io
    - [hostname].ca1cfd03.nip.io


- Deployment step for v1 (old) :
    - Edit file (stepx...) change namespace, hostname with your information of cluster
    - kubectl create -f step1-ns.yml
    - kubectl apply -f step2-cert-manager.yml
    - kubectl apply -f step3-uptime-app.yml
    - kubectl apply -f step4-ingress-prod.yml