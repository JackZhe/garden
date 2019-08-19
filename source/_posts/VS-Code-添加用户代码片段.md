---
title: VS Code 添加用户代码片段
date: 2019-08-14 12:11:05
tags:
  - vscode
categories:
  - 工具
---

## 代码片段

Visual Studio Code 昨天更新了，更新之后遇到了一个问题。之前在写 .vue 文件是 Vetur 有个 scaffold 可以快速生成代码结构。
更新之后发现不能用了，但是可以

{% asset_img 20190814121930.png %}

在微信群上有个死脑筋非要用之前的 scaffold，:worried:

于是我就想在 vscode 添加自定义的代码片段

> 文件 > 首选项 > 用户代码片段

{% asset_img 20190814122903.png %}

```json
  "Print to console": {
    "prefix": "log",
    "body": [
      "console.log('$1');",
      "$2"
    ],
    "description": "Log output to console"
  },
  "Vue Snippets": {
    "prefix": "scaffold",
    "body": [
      "<template>",
      "  <div>",
      "    $0",
      "  </div>",
      "</template> \n",
      "<script>",
      "export default {",
      "  name: '',",
      "",
      "}",
      "</script>\n",
      "<style lang='scss' scoped>\n",
      "</style>\n",
    ],
    "description": "Log output vue snippets"
  },
```

1. prefix: 触发快捷提示的字符串前缀

2. body: 代码片段的内容
3. \$1: 这个为光标的所在位置.
4. $2: 使用这个参数后会光标的下一位置将会另起一行,按tab键可进行快速切换,还可以有$3,$4,$5.....

5. description: 代码片段描述

### 补充 body

- $num 是每次按 tab 键光标移动对位置，$0  表示光标最后停留位置，不设置  \$0，这光标最终位置在文件末尾；
- \${2:默认文本}  跳转到指定位置到同时选中默认文本，方便修改；
- \$CURRENT_YEAR 是引用的 snippets 内置变量，其它还有：
- TM_FILENAME 当前文件名
- TM_FILENAME_BASE 当前文件名，不带扩展名
- TM_DIRECTORY 当前文件所属目录的绝对路径
- TM_FILEPATH 当前文件的绝对路径
- CURRENT_YEAR 当前年份
- CURRENT_YEAR_SHORT 当前年份，最后两位数字
- CURRENT_MONTH 当前月份数字形式，两位表示
- CURRENT_MONTH_NAME 当前月份英文形式，如 July
- CURRENT_MONTH_NAME_SHORT 当前月份英文缩写形式，如 Jul
- CURRENT_DATE 当前日
- CURRENT_DAY_NAME 当前星期，如 Monday
- CURRENT_DAY_NAME_SHORT 当前星期缩写形式，如 Mon
- CURRENT_HOUR 当前小时，24 小时格式，两位表示
- CURRENT_MINUTE 当前分钟，两位表示
- CURRENT_SECOND 当前秒，两位表示
- \n 换行
- \t 制表

```json
"Vue Snippets": {
    "prefix": "scaffold",
    "body": [
      "/**",
      " * $1",
      " * @author",
      " * @created $CURRENT_YEAR/$CURRENT_MONTH/$CURRENT_DATE $CURRENT_HOUR:$CURRENT_MINUTE:$CURRENT_SECOND",
      " */",
      "$2",
      "<template>",
      "  <div>",
      "    $0",
      "  </div>",
      "</template> \n",
      "<script>",
      "export default {",
      "  name: '',",
      "",
      "}",
      "</script>\n",
      "<style lang='scss' scoped>\n",
      "</style>\n",
    ],
    "description": "Log output vue snippets"
  },
```
