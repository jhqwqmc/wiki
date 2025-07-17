---
description: 此页显示所有可用的主机类型
---

# :wieless: 主机

{% hint style="success" %}
要应用对主机文件所作的更改，请执行命令“/ce 重新加载全部”。
{% endhint %}

{% hint style="danger" %}
DO NOT SHARE YOUR `config.yml` TO OTHERS\
Please use environment variables to prevent secret/token leakage
{% endhint %}

## 无

```yaml
类型：无
```

## 自己的

```yaml
type: self-
ip: localhost
port: 8163
protocol: http
deny-non-minecraft-request: true
one time-token: true
rate-limit:
  max-requests: 5
  重置间隔: 20 # 秒
```

{% hint style="warning" %}
**Using your server as a file host will consume some of its bandwidth.**\
You must set the IP to your server's actual address; otherwise, players won't be able to download resource packs!

不同于其他插件提供的 `self` 功能，**CraftEngine 为每个玩家生成一个独特和有时间限制和一次性的令牌**， 阻止所有未经授权的请求，以防止有针对性的交通攻击。 然而，这并不能保证绝对的安全——逆向工程袭击仍然是一种潜在的风险。
{% endhint %}

## 外部

```yaml
类型: 外部
url: ""
uuid: "" # 可选的
sha1: "" # 可选的
```

{% hint style="info" %}
**Host your resource pack on an external server.**\
This eliminates bandwidth consumption on your own server.

通常情况下，在将资源包上传到托管平台后，它将为您提供：

- **URL**
- **UUID (可选)**
- **SHA1 (可选)**

只需用相应的值填写这三个字段。
{% endhint %}

{% hint style="danger" %}
注意，要保持版本完整性，需要更新常规资源包。 这种维护程序需要人工干预。
{% endhint %}

## LobFile

```yaml
类型: lobfile
use-environment-variables: false
api-key: "xxx"
```

{% hint style="info" %}
**通过Lobfile管理您的资源包。**

当重新生成资源包时，插件将自动上传一个副本到 Lobfile. 与外部主机相比，这将消除手动上传。

_(注意：需要一个 API 键。 Visit_[ _lobfile_](https://lobfile.com/) _获取详细信息。)_
{% endhint %}

{% hint style="success" %}
环境变量

```
CE_LOBFILE_API_KEY
```

{% endhint %}

## OneDrive

```yaml
类型: onedrive
使用环境变量: false
client-id: ""
client-secret: ""
refresh-token: ""
upload-path: "server_resource_pack.zip"
```

{% hint style="success" %}
环境变量

```
CE_ONEDRIVE_CLIENT_ID
CE_ONEDRIVE_CLIENT_SECRET
CE_ONEDRIVE_REFRESH_TOKEN
```

{% endhint %}

## Dropbox

```yaml
类型: dropbox
使用环境变量: false
app-key : ""
app-secret: ""
refresh-token: ""
upload-path: "server_resource_pack.zip"
```

{% hint style="success" %}
环境变量

```
CE_DROPBOX_APP_KEY
CE_DROPBOX_APP_SECRET
CE_DROPBOX_REFRESH_TOKEN
```

{% endhint %}

## 闹钟

```yaml
type: alist
use-environment-variables: false
disable-upload: false
api-url: ""
用户名: ""
密码: ""
file-passed: ""
otp-code: ""
upload-path: "server_resource_pack. ix
```

{% hint style="success" %}
环境变量

```
CE_ALIST_USERNAME
CE_ALIST_PASWORD
CE_ALIST_FILE_PASWORD
```

{% endhint %}

## Gitlab

```yaml
类型：gitlab
使用环境变量：false
gitlab-url：""
存取令牌：""
项目 id：""
```

{% hint style="danger" %}
根据GitLab的服务条款，您无权使用 GitLab的服务器进行内容分配。 您必须设置自己的 GitLab 服务器来分配资源包。

[https://handbook.gitlab.com/handbook/legal/acceptable-use-policy/](https://handbook.gitlab.com/handbook/legal/acceptable-use-policy/)

> 我们通篇提到“我们的服务”——这意味着GitLab拥有或经营的所有服务(包括相关网站)。
>
> ...
>
> 3\. 因此，我们的服务和其他人的服务是安全的，在不受干扰的情况下，你不能：
>
> - 做任何事情来妥协、负担过重或以其他方式损害我们或他人的服务。 包括使用我们的服务来输入或展示加密货币或区块链的工作证明，或主要是为了传播内容。
>   {% endhint %}

{% hint style="success" %}
环境变量

```
CE_GITLAB_ACCESS_TOKEN
```

{% endhint %}

## s3

```yaml
类型: s3
终点: ""
bucket: ""
access-key-id: ""
access-key-secret: ""
protocol: "https"
path-style: false
region: "auto"
upload-path: "server_resource_pack. ip"
用法签名：true
validity: 10
cdn:
  domain: ""
  protocol: "https"
```

{% hint style="info" %}
\*\*当使用 S3 时，插件会通过为每个玩家生成独特和有时间限制的一次性下载链接来增强安全性。 \* 这使得攻击者无法获取固定的URL来发动攻击。 此外，插件在更新过程中自动处理资源包上传。
{% endhint %}

{% hint style="success" %}
环境变量

```
CE_S3_ACCESS_KEY_
CES3_ACCESS_KEY_SECRET
```

{% endhint %}

