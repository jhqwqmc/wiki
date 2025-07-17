---
description: This page shows all the available host types
---

# 🛜 Host

{% hint style="success" %}
To apply the changes made to the host file, execute the command `/ce reload all`.
{% endhint %}

{% hint style="danger" %}
DO NOT SHARE YOUR `config.yml` TO OTHERS\
Please use environment variables to prevent secret/token leakage
{% endhint %}

## None

```yaml
type: none
```

## Self

```yaml
type: self
ip: localhost
port: 8163
protocol: http
deny-non-minecraft-request: true
one-time-token: true
rate-limit:
  max-requests: 5
  reset-interval: 20 # seconds
```

{% hint style="warning" %}
**Using your server as a file host will consume some of its bandwidth.**\
You must set the IP to your server's actual address; otherwise, players won't be able to download resource packs!

Unlike the `self` feature offered by other plugins, **CraftEngine generates a unique & time-limited & one-time token for each player**, blocking all unauthorized requests to prevent targeted traffic attacks. However, this does not guarantee absolute security—reverse-engineering attacks remain a potential risk.
{% endhint %}

## External

```yaml
type: external
url: ""
uuid: "" # Optional
sha1: "" # Optional
```

{% hint style="info" %}
**Host your resource pack on an external server.**\
This eliminates bandwidth consumption on your own server.

Typically, after uploading your resource pack to a hosting platform, it will provide you with:

* **URL**
* **UUID (Optional)**
* **SHA1 (Optional)**

Simply fill these three fields with the corresponding values.
{% endhint %}

{% hint style="danger" %}
Note that regular resource pack updates are required to maintain version integrity. This maintenance procedure requires manual intervention.
{% endhint %}

## LobFile

```yaml
type: lobfile
use-environment-variables: false
api-key: "xxx"
```

{% hint style="info" %}
**Manage your resource packs via Lobfile.**

When regenerating resource packs, the plugin will automatically upload a copy to Lobfile. Compared to ExternalHost, this eliminates manual uploads.

_(Note: An API-KEY is required. Visit_[ _lobfile_](https://lobfile.com/) _for details.)_
{% endhint %}

{% hint style="success" %}
Enviroment Variables

```
CE_LOBFILE_API_KEY
```
{% endhint %}

## OneDrive

```yaml
type: onedrive
use-environment-variables: false
client-id: ""
client-secret: ""
refresh-token: ""
upload-path: "server_resource_pack.zip"
```

{% hint style="success" %}
Enviroment Variables

```
CE_ONEDRIVE_CLIENT_ID
CE_ONEDRIVE_CLIENT_SECRET
CE_ONEDRIVE_REFRESH_TOKEN
```
{% endhint %}

## Dropbox

```yaml
type: dropbox
use-environment-variables: false
app-key: ""
app-secret: ""
refresh-token: ""
upload-path: "server_resource_pack.zip"
```

{% hint style="success" %}
Enviroment Variables

```
CE_DROPBOX_APP_KEY
CE_DROPBOX_APP_SECRET
CE_DROPBOX_REFRESH_TOKEN
```
{% endhint %}

## Alist

```yaml
type: alist
use-environment-variables: false
disable-upload: false
api-url: ""
username: ""
password: ""
file-password: ""
otp-code: ""
upload-path: "server_resource_pack.zip"
```

{% hint style="success" %}
Enviroment Variables

```
CE_ALIST_USERNAME
CE_ALIST_PASSWORD
CE_ALIST_FILE_PASSWORD
```
{% endhint %}

## Gitlab

```yaml
type: gitlab
use-environment-variables: false
gitlab-url: ""
access-token: ""
project-id: ""
```

{% hint style="danger" %}
According to GitLab's Terms of Service, you are not permitted to use GitLab's servers for content distribution. You must set up your own GitLab server for distributing resource packs.

[https://handbook.gitlab.com/handbook/legal/acceptable-use-policy/](https://handbook.gitlab.com/handbook/legal/acceptable-use-policy/)

> We refer to “our services” throughout – this means all services (including related websites) owned or operated by GitLab.
>
> ...
>
> 3\. So our services, and those of others, run securely, and without disruption, you must not:
>
> * Do anything to compromise, overburden, or otherwise impair our services or those of others, including using our services to mine or demonstrate proof-of-work for a cryptocurrency or blockchain, or for the primary purpose of distributing content.
{% endhint %}

{% hint style="success" %}
Enviroment Variables

```
CE_GITLAB_ACCESS_TOKEN
```
{% endhint %}

## s3

```yaml
type: s3
endpoint: ""
bucket: ""
access-key-id: ""
access-key-secret: ""
protocol: "https"
path-style: false
region: "auto"
upload-path: "server_resource_pack.zip"
use-legacy-signature: true
validity: 10
cdn:
  domain: ""
  protocol: "https"
```

{% hint style="info" %}
**When using S3, the plugin enhances security by generating unique & time-limited & one-time download link for each player.** This prevents attackers from obtaining fixed URLs to launch attacks. Additionally, the plugin automatically handles resource pack uploads during updates.
{% endhint %}

{% hint style="success" %}
Enviroment Variables

```
CE_S3_ACCESS_KEY_ID
CE_S3_ACCESS_KEY_SECRET
```
{% endhint %}

