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