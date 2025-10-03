---
title: Yet Another Free AI
published: 2025-10-03
description: 介绍一下来着美团的免费ai--longcat，并申请更高每日额度
image: ./cover.png
tags:
  - AI
  - 白嫖
  - llm
  - longcat
category: AI
draft: false
---
刚才刷酷安的时候，看到了伞姨发的Longcat的动态，便想着拿来玩玩并水一篇blog。咕噜咕噜咕噜~
# 介绍
LongCat-Flash-Chat是由国内互联网大厂美团所开发一款**开源**的大语言模型。总参数 560B，激活参数 18.6B~31.3B
[数据来源](https://tech.meituan.com/2025/09/01/longcat-flash-chat.html)

# Api
各位最关心的应该就是api了
## 价格
目前Longcat的api**完全免费**！
新注册用户每日有500,000t免费额度，经过毫无门槛的申请过后升级为5,000,000t/日
*目前api额度无法购买*
:::tip
- 输入和输出Tokens均计入消耗
- 流式接口和段式接口消耗相同
:::
## 接口格式
- 完全兼容OpenAI API规范
- 兼容Anthropic Claude API规范

## 限制
目前输出限制为8k

## AI Agent
目前暂时还没看到支持Agent的迹象，但是API支持Claude Code CLI

# 额度申请
目前额度申请非常简单，任何材料都不需要，几乎没有审核。
伞姨的图文说
> 只要填你是学校的科研需要或者实验室项目就可以秒通过申请了

我自己填的是互联网公司，公司开展ai相关业务需要。最终也通过了