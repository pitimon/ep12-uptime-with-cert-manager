Uptime kuma deployment v3 for:

- Cluster POP22's member
- Ubuntu/Debian kubuctl client
- [APPNAME].3.ipv9.me via Cloudflare Proxy.

## Pre-Deployment
Ubuntu/Debian requires [gettext](https://zoomadmin.com/HowToInstall/UbuntuPackage/gettext) to run

```sh
sudo apt-get update
sudo apt-get install -y gettext
```

## Variable environments
| Plugin | README |
| ------ | ------ |
| APPNAME | Application_name and [hostname].ipv9.me |
| PROJECTID | Get projectId from rancher web mgmt |
| CLOUDFLARED_TOKEN | Create Cloudflare Zero Trust tunnel |

## Deployment app
edit before use:

```sh
export APPNAME="[choose APP name]"
export PROJECTID="[Your ProjectId from Rancher web]"
```

```sh
envsubst < step1-namespace.yml | kubectl create -f -
```

```sh
envsubst < step2-uptime-app.yml | kubectl apply -f - 
kubectl rollout status -n uptime-$APPNAME deployment $APPNAME
```

## Remove namespace all
export APPNAME="[chose APP name]"
export PROJECTID="[Your ProjectId from Rancher web]"

```sh
envsubst < step1-namespace.yml | kubectl delete -f -
```
>> Good luck...
