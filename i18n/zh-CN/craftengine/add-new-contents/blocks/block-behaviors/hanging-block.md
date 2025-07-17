# 🚟 悬挂块

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FJeuDs9y5sL36WOa0fB4x%2Fimage.png?alt=media&#x26;token=049ac4d9-aee7-4605-b6f1-5debd761f33c" alt=""><figcaption></figcaption></figure>

[hanging-block](hanging-block "提及") 是一种必须附加在另一个方块下方的方块类型。 如果上面的方块被摧毁，挂起方块本身也会被中断。

```yaml
blocks:
  default:stalactivity:
    行为:
      类型: hanging_block
      stack: false
      blacklist: false # 使用黑名单模式
      上方块标签: []
      上方块: []
      延迟: 0
```
