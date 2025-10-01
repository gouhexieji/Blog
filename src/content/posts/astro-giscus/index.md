---
title: 为你的Blog添加giscus评论
published: 2025-10-01
description: Astro博客框架添加基于giscus的评论系统
image: ./cover.png
tags:
  - blog
  - astro
  - giscus
category: 主题魔改
draft: false
---
最近把博客的主题从Akiba换到了功能更加完善的Fuwari，非常蛋疼的是，Fuwari默认并不支持任何一款评论系统。想要评论，只能对源码进行一些修改。
好在有现成的[作业](https://f.1.5.0.9.1.0.0.0.7.4.0.1.0.0.2.ip6.arpa/posts/comment/)可以抄 ~~Good-Github-Copy-And-Paste~~

# Giscus

先在Github创建一个**公开**的仓库并**开启评论**用来存放评论。
> 该仓库**必须**是公开的，否则访客将无法查看 discussion。

然后在[这里](https://github.com/apps/giscus)安装Giscus App
在这里填入用来存储评论的仓库
![](repo—url.png)
映射填`pathname`：以文章路径区分评论区，即使换域名也能匹配
特性我只开启了懒加载
生成的js应该如下所示
```
<script src="https://giscus.app/client.js"
        data-repo="YOUR_REPO_NAME"
        data-repo-id="REPO_ID"
        data-category="Announcements"
        data-category-id="CATEGORY_ID"
        data-mapping="title"
        data-strict="0"
        data-reactions-enabled="1"
        data-emit-metadata="0"
        data-input-position="top"
        data-theme="preferred_color_scheme"
        data-lang="zh-CN"
        data-loading="lazy"
        crossorigin="anonymous"
        async>
</script>
```

# Astro的魔改
## 创建Giscus的预制代码
在`src`目录下的`components`目录中新建Giscus.astro
把上面生成的js粘贴进去
##  修改文章页面

找到负责渲染文章的 astro 文件，其应该在`pages`目录下（这其实与其他框架是类似的，也就是网站由 “页面” 构成，其中会有一个页面是显示文章的）

在 Fuwari 主题中，其应该在`src`->`pages`->`posts`->`[...slug].astro`，对其进行修改：
```
---
import CommentSection from '@components/Giscus.astro'
---
...
	<!-- 文章渲染主元素 -->
	<div>
		...
		<!-- 最后一个元素 -->
		<div>
			...
		</div>
		<CommentSection />
	</div>
...

```
如果以 Fuwari 主题为例，其应该放置在版权信息下
```
<div>
	...
	
	{licenseConfig.enable && <License ...></License>}
	
	<CommentSection />
</div>

```
应该就可以了
![](cover.png)

# 一些问题
由于Giscus的js并没有使用主题的css,所以在某些情况下，比如说深色模式下有些文字和太刺眼/难以看清，还需要进一步的优化。