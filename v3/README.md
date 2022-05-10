# appname and [hostname].3.ipv9.xyz
export APPNAME="env101"
# get projectId from rancher web mgmt
export PROJECTID="c-m-7l8v45x2:p-z5t58"
# your email for sign Let's
export MYEMAIL="ip@en.rmutt.ac.th"
# cert state [staging/prod]
export CERTSTATE="staging"

envsubst < MASTER-step1-namespace.yml | kubectl create -f -

envsubst < MASTER-step2-app.yml | kubectl apply -f - 