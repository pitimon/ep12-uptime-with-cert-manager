Uptime kuma deployment v3 for:

- Cluster POP22's member
- Ubuntu/Debian kubuctl client
- [APPNAME].ipv9.me via Cloudflare Zero Trust.

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
| CLOUDFLARED_TOKEN | Create Cloudflare Zero Trust tunnel |

## Deployment app
edit before use:

export APPNAME="[chose APP name]"
export PROJECTID="[Your ProjectId from Rancher web]"
export CLOUDFLARED_TOKEN="[CreateTunnelZeroTrust before]"

```sh
envsubst < step1-namespace.yml | kubectl create -f -
```

```sh
envsubst < step2-uptime-app.yml | kubectl apply -f - 
kubectl rollout status -n uptime-$APPNAME deployment $APPNAME
```
>> At cloudflare zero trust mgmt:
    - update Access>Tunnels>[xxx]>Public Hostname>Service HTTP {APPNAME}:3001

## Remove namespace all
export APPNAME="[chose APP name]"
export PROJECTID="[Your ProjectId from Rancher web]"

```sh
envsubst < step1-namespace.yml | kubectl delete -f -
```
>> Good luck...
