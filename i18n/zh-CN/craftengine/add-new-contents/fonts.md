---
description: 此页面主要说明如何添加新字体
---

# 秘️ Fonts

## TTF

{% embed url="https://minecraft.wiki/w/Font#TTF_provider" %}

对于TTF 字体，您需要在下面的路径中创建 `default.json` 文件。 如果您已经有一个 `default.json` 文件，只需将您的 JSON 字体附加到现有JSON 文件的底部。

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FiIqkr8gniPWWU3QCYKIS%2Fimage.png?alt=media&#x26;token=7c94e751-1cf2-4b1c-875d-39a7e7346f58" alt=""><figcaption></figcaption></figure>

<pre class="language-json"><code class="lang-json">A format@@1 // 默认。 Son
</strong>Power
    "providers": [
        vol.
            "ttf",
            "file": "minecraft:custom_font tf",
            "过多采样": 10,
            "大小"：11
        }

}
</code></pre>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FTKv2B9h3sS7TVSgIJkaA%2Fimage.png?alt=media&#x26;token=10a0ea88-c186-4638-9946-e3c98844c94b" alt=""><figcaption></figcaption></figure>

## Bitmap

{% 嵌入的 url="https://minecraft.wiki/w/Font#Bitmap_provider" %}

如果您想要替换原版字符图像，请将以下PNG文件放置在下面概述的指定路径中。

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2Fb4x0H5SUIl3TSku2UKHa%2Fimage.png?alt=media&#x26;token=bffc7f87-97f0-4e5f-af5c-735ad8189d60" alt=""><figcaption></figcaption></figure>

## Unihex

要在Minecraft中配置 `unihex` 字体，这个字体相对较少，很少使用，您可以参考MinecraftWiki 获取详细说明。

{% 嵌入的 url="https://minecraft.wiki/w/Font#Unhex_provider" %}

```json
{
    "providers": [
        {
            "type": "unihex",
            "hex_file": "minecraft:font/unifont_jp.zip",
            "size_overrides": [
                {
                    "__ranges": [
                        "Enclosed CJK Letters and Months",
                        "CJK Compatibility",
                        "CJK Unified Ideographs Extension A",
                        "Yijing Hexagram Symbols",
                        "CJK Unified Ideographs"
                    ],
                    "from": "\u3200",
                    "to": "\u9FFF",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "CJK Compatibility Ideographs"
                    ],
                    "from": "\uF900",
                    "to": "\uFAFF",
                    "left": 0,
                    "right": 15
                }
            ],
            "filter": {
                "jp": true
            }
        },
        {
            "type": "unihex",
            "hex_file": "minecraft:font/unifont.zip",
            "size_overrides": [
                {
                    "__ranges": [
                        "CJK Symbols and Punctuation",
                        "Hiragana",
                        "Katakana"
                    ],
                    "from": "\u3001",
                    "to": "\u30FF",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "Enclosed CJK Letters and Months",
                        "CJK Compatibility",
                        "CJK Unified Ideographs Extension A",
                        "Yijing Hexagram Symbols",
                        "CJK Unified Ideographs"
                    ],
                    "from": "\u3200",
                    "to": "\u9FFF",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "Hangul Jamo"
                    ],
                    "from": "\u1100",
                    "to": "\u11FF",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "Hangul Compatibility Jamo"
                    ],
                    "from": "\u3130",
                    "to": "\u318F",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "Hangul Jamo Extended-A"
                    ],
                    "from": "\uA960",
                    "to": "\uA97F",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "Hangul Jamo Extended-B"
                    ],
                    "from": "\uD7B0",
                    "to": "\uD7FF",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "Hangul Syllables",
                    ],
                    "from": "\uAC00",
                    "to": "\uD7AF",
                    "left": 1,
                    "right": 15
                },
                {
                    "__ranges": [
                        "CJK Compatibility Ideographs"
                    ],
                    "from": "\uF900",
                    "to": "\uFAFF",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "Halfwidth and Fullwidth Forms"
                    ],
                    "from": "\uFF01",
                    "to": "\uFF5E",
                    "left": 0,
                    "right": 15
                }
            ]
        }
    ]
}
```
