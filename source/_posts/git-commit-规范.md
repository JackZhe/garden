---
title: git commit 规范
date: 2019-08-20 22:17:39
tags:
  - git
categories:
  - 工具
---

以 Angular 的 Git commit 日志为基本规范

## 消息组成

```code
<type>(<scope>): <subject> #header
< 空行 >
body
< 空行 >
footer
```

### type

type 提交类型

- feat: 新功能（feature）
- fix: 修补 bug
- docs: 修改了文档 eg: README
- style: 修改空格 缩进，不改变代码逻辑
- refactor: 代码重构，没有添加新功能，没有修补 bug
- perf: 优化相关，eg: 提升性能，体验
- test: 增加测试，eg: 单元测试，集成测试
- chore: 改变构建流程或者增加依赖库，工具
- revert: 回滚到上一个版本

### scope

scope 修改了哪部分指范围 主要是这次修改涉及到的部分，最好简单的概括

### subject

subject 修改的副标题 主要是具体修改的加点

```bash
$ git commit -m 'doc: 修改了readme'
$ git commit -m 'fix+style: 修改了safari 3D transform造成的z-index bug和 导航条样式'
```

## [commitlint](https://github.com/conventional-changelog/commitlint)

用来规范团队的 git 提交信息

```bash
# Install commitlint cli and conventional config
npm install --save-dev @commitlint/{config-conventional,cli}
# For Windows:
npm install --save-dev @commitlint/config-conventional @commitlint/cli

# Configure commitlint to use conventional config
echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js
```

在根目录添加 commitlint.config.js

{% asset_img 20190821143753.png %}

## 验证 message 格式

[husky](https://github.com/typicode/husky) 是一个 git hook 的管理工具

```Json package.json
{
  "husky": {
    "hooks": {
      "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
    }
  }
}
```

```bash bad
$ git commit -m '添加代码规范'
husky > commit-msg (node v10.15.3)
⧗   input: 添加代码规范
✖   subject may not be empty [subject-empty]
✖   type may not be empty [type-empty]

✖   found 2 problems, 0 warnings
ⓘ   Get help: https://github.com/conventional-changelog/commitlint/#what-is-commitlint

husky > commit-msg hook failed (add --no-verify to bypass)
```

提示 type 和 subject 没有写，规范提交

```bash good
$ git commit -m 'chore: 添加代码规范'
husky > commit-msg (node v10.15.3)
[dev1.1 64fa189] chore: 添加代码规范
 3 files changed, 981 insertions(+)
 create mode 100644 commitlint.config.js
```

header 部分大概 50 个字符就可以简介概要表述要提交的东西

## 合格的 message 格式

撰写合格 Commit message 的工具

```bash
$ npm install -g commitizen

#支持 Angular 的 Commit message 格式
$ commitizen init cz-conventional-changelog --save --save-exact
```

使用 git commit 更改为 cz 会出现选项，用来生成符合格式的 Commit message

## Change log

conventional-changelog-cli 生成 Change log 的工具

```bash
$ npm install -g conventional-changelog-cli
$ conventional-changelog -p angular -i CHANGELOG.md -s -w -r 0

```

```json
{
  "scripts": {
    "changelog": "conventional-changelog -p angular -i CHANGELOG.md -s -w -r 0"
  }
}
```

```code
$ npm run changelog

```
