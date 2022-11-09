---
title: Github search tips
date: 09-11-2022 
categories:
- Github 
tags:
- Github
---

当我还是一个开源贡献的初学者时，我最大的挑战之一是找到正确的项目/issue 来为其做贡献。

在很长一段时间里，我依靠互联网上不同作者创作的资源（顺便说一下，这些资源很好）。但我一直想找到一种解决这个问题的方法——一种我可以搜索和跟踪适合我的技能组合的项目的方法。

让我们承认一件事：与谷歌不同，在 GitHub 上搜索并不容易。但作为一个开发者，你有可能每天都会与 GitHub 或 GitLab 打交道。

现在的问题不是你用这些版本控制系统做什么，而是你如何使用它们。就像掌握谷歌搜索技巧对任何普通互联网用户来说都是必不可少的，我相信对于开发者来说，学会如何有效地在 GitHub 搜索也是至关重要的。

在这篇文章中，我们将看看可以用来正确地在 GitHub 搜索的不同技巧。你将学习如何通过搜索：


- 问题（issues）和拉取请求（pull requests）
- 仓库（repositories）
- 用户（users）
- 主题（topics）

## GitHub 搜索查询
为了在互联网上找到关于某件事情的详细信息，你需要有正确的搜索技巧。这在 GitHub 上没有任何不同——要找到详细的信息，你可以利用常见的过滤、排序和搜索技术，轻松找到特定项目的 issues 和 pull requests。

即使你能在互联网上找到许多不同项目的资源，但当你想自己进行搜索时，主要问题就来了：你该如何开始？你应该使用哪些关键词来找到正确的结果？

大多数维护者倾向于用 issues 来标记他们的项目，这使得贡献者更容易找到合适的项目。下面列出了一些在使用 GitHub 时可能会对你有所帮助的小技巧。


## 如何在 GitHub 上搜索 issues 和 pull requests
搜索 issues 和相关的 pull requests，是寻找要贡献的项目的最常见的方法之一。这里有一些技巧，你可以用来轻松找到可靠的答案：

1、`is:issue is:open label:beginner`——这个特别的查询会列出所有具有开放的、并标有 `beginner` 的 issues 的项目。

2、`is:issue is:open label:easy`——这将列出所有被标记为 `easy` 的开放 issues。

3、`is:issue is:open label:first-timers-only`——这将列出所有欢迎第一次做贡献的人们的开放 issues。

4、`is:issue is:open label:good-first-bug`——这将列出带有 `good-first-bug` 标签的开放 issues 的项目，以吸引贡献者为其工作。

5、`is:issue is:open label:"good first issue"`——这将列出所有带有 `good first issue` 标签的开放 issues，意味着它是初学者入门的好地方。

6、`is:issue is:open label:starter`——这将列出整个 GitHub 中所有标有 `starter` 的开放 issues。

7、`is:issue is:open label:up-for-grabs`——这将列出开放的 issues，如果你有必要的技能，就可以进行工作。

8、`no:project type:issue is:open`——这将列出所有没有分配给特定项目的开放 issues。

9、`no:milestone type:issue is:open`——很多时候，项目是用里程碑来追踪的。但如果你想找到没有被跟踪的 issues，这个搜索查询将为你列出这些项目。

## 如何搜索仓库
默认情况下，要进行搜索，你需要在搜索栏中输入仓库的名称，然后就可以得到一些搜索结果。

但你找到你想要的仓库的机会非常低。

让我们看看有什么方法可以缩小搜索范围：

### 如何通过名称、描述/README 查找
当你通过 README 文件的名称和描述进行搜索时，需要注意的是，你的搜索短语应该以 in 限定词开始。这样就可以在你要找的东西的“内部”进行搜索。

#### 示例

- 使用 `in:name`。比方说，你正在寻找资源，以了解更多关于数据科学的信息。在这种情况下，你可以使用 Data Science in:name 命令，它将列出仓库名称中含有 Data Science 的仓库。

- 使用 `in:description`。如果你想找到具有特定描述的仓库，例如，仓库的描述中包含 “freeCodeCamp” 一词，我们的搜索将是：freecodecamp in:description。

- 使用 `in:readme`。你用它来搜索一个文件的 README 中的某一短语。如果我们想找到 README 中包含 freecodecamp 这个词的仓库，我们的搜索将是：freecodecamp in:readme。

- 使用 `in:topic`。你用它来查找某个短语或单词是否被标注在主题中。例如，要找到所有在主题中列出 freecodecamp 的仓库，我们的搜索将是：`freecodecamp in:topic`。

你也可以结合多个搜索查询，进一步缩小搜索范围。

### 如何按 Stars、Forks 查找
你也可以根据项目的 star 和 fork 的数量来搜索仓库。这使你更容易知道该项目有多受欢迎。

#### 示例

- 使用 `stars:n`。如果你搜索一个有 1000 star 的仓库，那么你的搜索查询将是 `stars:1000`。这将列出正好有 1000 star 的仓库。

- 使用 `forks:n`。这指定了一个仓库应该有的 fork 数。如果你想找到少于 100 个 fork 的仓库，你的搜索将是：`forks:<100`。

你可以随时使用关系运算符，如 <、>、<=、>= 和 .. 来帮助你进一步缩小搜索范围。

### 如何按语言查找
在 GitHub 上搜索的另一个很酷的方法是按语言搜索。这可以帮助你过滤出特定语言的仓库。

#### 示例

- 使用 `language:LANGUAGE`。例如，如果你想找到用 PHP 编写的仓库，你的搜索将是：`language:PHP`。
- 
### 如何按组织名称查找
你也可以搜索由一个特定组织维护或创建的仓库/项目。为此，你需要用关键词 `org:...` 来开始你的搜索，然后是组织名称。

例如，如果你搜索 `org:freecodecamp`，它将列出与 freeCodeCamp 相匹配的仓库。

### 如何按日期查找
如果你希望你的结果基于一个特定的日期，你可以使用这些关键词之一进行搜索：`created、updated、merged` 和 `closed`。这些关键词应该伴随着格式为 `YYYY-MM-DD` 的日期一起使用。

#### 示例

使用 `keyword:YYYY-MM-DD`。举个例子，我们想搜索所有在 2022-10-01 之后创建的带有 freeCodeCamp 这个词的仓库。那么我们的搜索将是：`freecodecamp created:>2022-10-01`。

你也可以使用 `<、>、>= `和 `<= `来搜索指定日期之后、之前和指定日期的日期。要在一个范围内搜索，你可以使用 `...`。

### 如何通过许可证查找
当你在寻找一个可以贡献的项目时，许可证是非常重要的。不同的许可证对贡献者可以做什么或不可以做什么给予不同的权利。

为了使你更容易找到有正确许可证的项目，你需要对许可证有一个很好的了解。你可以在这里阅读更多关于它们的信息。

#### 示例

- 使用 `license:LICENSE_KEYWORD`。这是一个搜索具有特定许可证的项目的好方法。例如，要搜索具有 MIT 许可证的项目，你可以使用 `license:MIT`。
  
### 如何按可见性搜索
你也可以根据仓库的可见性来进行搜索。在这种情况下，你可以使用 `public` 或者 `private`。这将分别匹配公共或私人仓库中的 `issues` 和 `pull requests`。

#### 示例

- 使用 `is:public`。这将显示一个公共仓库的列表。让我们举个例子，我们想搜索所有由 freeCodCamp 拥有的仓库。那么我们的搜索将是：`is:public org:freecodecamp`。

- 使用 `is:private`。这个查询是为了列出所有在给定的搜索查询下的私有仓库。

