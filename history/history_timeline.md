# history_timeline

## 数据结构

```ts
type TextWithLink = {
      text: string,
      href: string,
      describe?: string
    }

type ParaWithLink = TextWithLink | string

type Paragraph = ParaWithLink[] | string

type HistoryTitle = {
      type: 'primary',
      content: string
    }

type HistoryContent = {
      type: '',
      timestamp: string,
      title: string
      describe: string,
      content: Paragraph[]
    }

type TimelineLine = HistoryTitle | HistoryContent

var history_timeline: TimelineLine[]
```

``` json5
[
  {                                    // 一个时间线标题项目
    "type": "primary"
    "content": "标题"
  },
  {                                    // 一个时间线内容项目
    "type": ""
    "timestamp": "yyyy-mm-dd"          // 其实是时间字符串，不是时间戳
    "title": "标题"
    "describe": "标题下面的灰色斜体字"
    "content": [                       // 内容：每一项都是一个段落
        "段落一",                         // 段落可以是一个字符串
        [                              // 或者一个包含“带超链接的文本”的数组
            "段落二，",                    // 这个文本是段落的一部分，不会换行
            {                          // 这是一个“带超链接的文本”
                "href": "...",         // 链接地址
                "text": "这是一个超链接，"      // 链接文本
            },
            "仍然是段落二，",
            {
                "href": "...",
                "text": "可以有任意个链接，",
                "describe": "可选参数，鼠标悬停时显示"
            }
        ]
    ]
  }
  // ...
]
```
