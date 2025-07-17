---
description: This page mainly tells how to add a new font
---

# ㊙️ Fonts

## TTF

{% embed url="https://minecraft.wiki/w/Font#TTF_provider" %}

For TTF fonts, you need to create a `default.json` file in the following path. If you already have a `default.json` file, simply append your font JSON to the bottom of the existing JSON file.

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FiIqkr8gniPWWU3QCYKIS%2Fimage.png?alt=media&#x26;token=7c94e751-1cf2-4b1c-875d-39a7e7346f58" alt=""><figcaption></figcaption></figure>

<pre class="language-json"><code class="lang-json"><strong>// default.json
</strong>{
    "providers": [
        {
            "type": "ttf",
            "file": "minecraft:custom_font.ttf",
            "oversample": 10,
            "size": 11
        }
    ]
}
</code></pre>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FTKv2B9h3sS7TVSgIJkaA%2Fimage.png?alt=media&#x26;token=10a0ea88-c186-4638-9946-e3c98844c94b" alt=""><figcaption></figcaption></figure>

## Bitmap

{% embed url="https://minecraft.wiki/w/Font#Bitmap_provider" %}

If you wish to replace the vanilla character images, simply place the following PNG files in the specified path as outlined below.

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2Fb4x0H5SUIl3TSku2UKHa%2Fimage.png?alt=media&#x26;token=bffc7f87-97f0-4e5f-af5c-735ad8189d60" alt=""><figcaption></figcaption></figure>

## Unihex

To configure the `unihex` font in Minecraft, which is relatively less common and rarely used, you can refer to the Minecraft Wiki for detailed instructions.

{% embed url="https://minecraft.wiki/w/Font#Unihex_provider" %}

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
