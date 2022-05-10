## Variable environments
| Plugin | README |
| ------ | ------ |
| APPNAME | application name and [hostname].3.ipv9.xyz |
| PROJECTID | get projectId from rancher web mgmt |
| MYEMAIL | sign Let's Encrypt |
| CERSTATE | staging/prod |

## Deployment app
```sh
export APPNAME="env101"
export PROJECTID="c-m-7l8v45x2:p-z5t58"
export MYEMAIL="ip@en.rmutt.ac.th"
export CERTSTATE="staging"
envsubst < step1-namespace.yml | kubectl create -f -
envsubst < step2-uptime-app.yml | kubectl apply -f - 
kubectl rollout status -n uptime-$APPNAME deployment $APPNAME
```

## Remove
```sh
export APPNAME="env101"
export PROJECTID="c-m-7l8v45x2:p-z5t58"
export MYEMAIL="ip@en.rmutt.ac.th"
export CERTSTATE="staging"
envsubst < step2-uptime-app.yml | kubectl delete -f - 
envsubst < step1-namespace.yml | kubectl delete -f -
```