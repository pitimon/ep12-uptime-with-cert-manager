# appname and [hostname].3.ipv9.xyz
export APPNAME="env101"
# get projectId from rancher web mgmt
export PROJECTID="c-m-7l8v45x2:p-z5t58"
# your email for sign Let's
export MYEMAIL="ip@en.rmutt.ac.th"
# cert state [staging/prod]
export CERTSTATE="staging"
# Deployment app
envsubst < step1-ns.yml | kubectl create -f -
envsubst < step2-app.yml | kubectl apply -f - 
kubectl rollout status -n uptime-$APPNAME deployment $APPNAME

# Remove
# appname and [hostname].3.ipv9.xyz
export APPNAME="env101"
# get projectId from rancher web mgmt
export PROJECTID="c-m-7l8v45x2:p-z5t58"
# your email for sign Let's
export MYEMAIL="ip@en.rmutt.ac.th"
# cert state [staging/prod]
export CERTSTATE="staging"
# deployment 2 step
envsubst < step2-app.yml | kubectl delete -f - 
envsubst < step1-ns.yml | kubectl delete -f -
