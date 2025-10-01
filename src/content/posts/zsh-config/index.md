---
title: 从零开始的zsh配置指南
published: 2025-09-01
description: zsh配置指南
image: ./cover.png
tags: [zsh,linux,shell]
category: "linux"
draft: false
---
# 从零开始的zsh配置指南
最近重装了下Arch，记录一下配置zsh的过程(~~水一篇Blog~~。
## 安装zsh🛠
```
sudo pacman -S zsh zsh-completions
```
> zsh-completions是一个zsh的自动补全增强模块
## 更改默认shell🔄
在Arch下，新用户的默认shell是bash，需要手动切换为zsh
```
chsh
```
> 这里不能直接输入zsh要输入zsh二进制文件的绝对路径。如/bin/zsh
## 安装oh-my-zsh🛠
> Oh My Zsh is a delightful, open source, community-driven framework for managing your Zsh configuration. It comes bundled with thousands of helpful functions, helpers, plugins, themes, and a few things that make you shout...
> Oh My Zsh 是一个令人愉悦的、开源的、由社区驱动的框架，用于管理你的 Zsh 配置。它自带了成千上万个实用的函数、辅助工具、插件、主题，以及一些能让你忍不住惊呼的东西……

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

虽然omz一直以为它的性能问题被诟病，但我自己用习惯了，你也可以换成zim.fw之类的。

## 一些插件推荐🔌
### zsh-autosuggestions
zsh-autosuggestions 是一个命令提示插件，当你输入命令时，会自动推测你可能需要输入的命令，按下右键可以快速采用建议。
```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
### zsh-syntax-highlighting
zsh-syntax-highlighting 是一个命令语法校验插件，在输入命令的过程中，若指令不合法，则指令显示为红色，若指令合法就会显示为绿色。
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
### fzf-tab
用 fzf 替换 zsh 默认的补全选择菜单！
```
sudo pacman -S fzf
```
首先需要安装fzf
```
git clone https://github.com/Aloxaf/fzf-tab ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/fzf-tab
```

最后更改zshrc的plugin字段
```
plugins=(git z x fzf-tab zsh-syntax-highlighting zsh-autosuggestions )
```

## Starship🚀
我并不像使用烂大街的p10k主题，其他的zsh主题也没有让我觉得好看的，故这里使用Starship。
Starship是一个独立的软件包，并且包含在arch extra源中。
```
sudo pacman -S starship
```
在zshrc的末尾添加
```
eval "$(starship init zsh)"
```

大多数Starship主题需要Nerd Font
我这里推荐[Agave](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/Agave)
```
sudo pacman -S ttf-agave-nerd
```

 https://starship.rs/presets/ 这里有很多Starship的主题。我选择了Gruvbox Rainbow。
 ```
 starship preset gruvbox-rainbow -o ~/.config/starship.toml
 ```

## 大功告成🎉
重新启动一个shell 试试效果吧
