Uptime kuma deployment v3 for:

- Cluster POP22's member
- Ubuntu/Debian kubuctl client
- [hostname].3.ipv9.xyz via external layer 4 loadbalance

## Pre-Deployment
Ubuntu/Debian requires [gettext](https://zoomadmin.com/HowToInstall/UbuntuPackage/gettext) to run
```sh
sudo apt-get update
sudo apt-get install -y gettext
```

## Variable environments
| Plugin | README |
| ------ | ------ |
| APPNAME | Application_name and [hostname].3.ipv9.xyz |
| PROJECTID | Get projectId from rancher web mgmt |
| MYEMAIL | Sign Let's Encrypt |
| CERTSTATE | Select staging/prod |

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
