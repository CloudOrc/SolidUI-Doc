# 如何参与项目贡献

非常感谢贡献 SolidUI 项目！在参与贡献之前，请仔细阅读以下指引。

## 一、贡献范畴

### 1.1 Bug 反馈与修复

我们建议无论是 Bug 反馈还是修复，都先创建一个 Issue 来仔细描述 Bug 的状况，以助于社区可以通过 Issue 记录来找到和回顾问题以及代码。Bug 反馈 Issue 通常需要包含**完整描述 Bug 的信息**以及**可复现的场景**，这样社区才能快速定位导致 Bug 的原因并修复它。包含 `#bug` 标签的打开的 Issue 都是需要被修复的。

### 1.2 功能交流、实现、重构

在交流过程中，详细描述新功能（或重构）的细节、机制和使用场景，能够促使它更好更快地被实现（包括测试用例和代码，及 CI/CD 相关工作）。**如果计划实现一个重大的功能（或重构），请务必通过 Issue 或其他方式与核心开发团队进行沟通**，这样大家能以最效率的方式来推进它。包含 `#feature` 标签的打开的 Issue 都是需要被实现的新功能，包含 `#enhancement` 标签打开的 Issue 都是需要改进重构的功能。

### 1.3 Issue 答疑

帮助回答 Issue 中的使用问题是为 SolidUI 社区做贡献的一个非常有价值的方式；社区中总会有新用户不断进来，在帮助新用户的同时，也可以展现您的专业知识。

### 1.4 文档改进

SolidUI 文档位于[SolidUI_Doc](https://github.com/CloudOrc/SolidUI-Doc) ，文档的补充完善对于 SolidUI 的发展也至关重要。

### 1.5 其他

包括参与和帮助组织社区交流、社区运营活动等，其他能够帮助 SolidUI 项目和社区的活动。

## 二、贡献流程

### 2.1 分支结构

SolidUI 源码可能会产生一些临时分支，但真正有明确意义的只有以下三个分支：

- release-*: 稳定的 release 版本；
- dev: 日常开发分支，也是大家贡献代码的目标分支，如果你想贡献代码，请基于 dev 分支创建新分支，版本发布时会基于dev新建release分支；

#### 2.1.1 概念

- Upstream 仓库:<https://github.com/CloudOrc/SolidUI> SolidUI 仓库文中称为 Upstream 仓库
- Fork 仓库: 从 <https://github.com/CloudOrc/SolidUI> fork 到自己个人仓库 称为 Fork 仓库

#### 2.1.2 同步 Upstream 仓库分支最新代码到自己的 Fork 仓库

- step1 进入用户项目页面,选中要更新的分支
- step2 点击 code 下载按钮下方的 Fetch upstream,选择 Fetch and merge (如自己的 Fork 仓库  该分支不小心污染了，可以删除该分支后，同步 Upstream 仓库新分支到自己的 Fork 仓库  ，参见指引[同步 Upstream 仓库分支最新代码到自己的 Fork 仓库  ](#213-同步 Upstream 仓库新分支到自己的 Fork 仓库  ))


#### 2.1.3 同步 Upstream 仓库新分支到自己的 Fork 仓库

场景：Upstream 仓库有新增分支，但是 fork 的库没有该分支 (可以选择删除后，重新 fork，但是会丢失未 merge 到原始仓库的变更)


* step1 打开 Git 命令行工具（如 Git Bash），克隆自己的 Fork 仓库到本地
```
git clone https://github.com/{your_github_username}/SolidUI.git
```

* step2 进入本地仓库目录
```
cd SolidUI
```

* step3 添加 Upstream 仓库为远程仓库
```
git remote add upstream https://github.com/CloudOrc/SolidUI.git
```

* step4 获取 Upstream 仓库的分支信息
```
git fetch upstream
```

* step5 同步 Upstream 仓库的新分支到本地
```
git checkout -b {new_branch_name} upstream/{new_branch_name}
```
* step6 将新分支推送到自己的 Fork 仓库
```
git push --set-upstream origin {new_branch_name}
```

#### 2.1.4 一个 pr 的流程

- step1 确认当前开发的基础分支（一般是当前进行的中版本，如当前社区开发中的版本 0.2.0，那么分支就是 dev，不确定的话可以在社区群里问下或则在 issue 中@相关同学）

- step2 同步 Upstream 仓库分支最新代码到自己的 Fork 仓库 分支,参见指引 [2.1.2 同步 Upstream 仓库分支最新代码到自己的 Fork 仓库 ]

- step3 基于开发分支，拉取新 fix/feature 分支 (不要直接在原分支上修改，如果后续 pr 以 squash 方式 merge 后，提交的 commit 记录会被合并成一个)

```shell script
git checkout -b dev-fix  dev
git push origin dev-fix:dev-fix
```

- step4  进行开发
- step5  提交 pr(如果是正在进行中,开发还未完全结束，请在 pr 标题上加上 WIP 标识 如 `[WIP] Dev 0.2.0 Add junit test code for [solidui-common]` ;关联对应的 issue 等)
- step6  等待被合并
- step7  删除 fix/future 分支 (可以在 github 页面上进行操作)

```shell script
git branch -d dev-fix
git push
```


### 2.2 开发指引

SolidUI 前后端代码共用同一个代码库，但在开发上是分离的。在着手开发之前，请先将 SolidUI 项目 fork 一份到自己的 Github Repositories 中， 开发时请基于自己 Github Repositories 中的 SolidUI 代码库进行开发。

我们建议克隆 dev 分支命名为 dev-fix 来开发,同时在自己仓库新建 dev-fix 分支，直接在原分支上修改，如果后续 pr 以 squash 方式 merge 后，提交的 commit 记录会被合并成一个

```shell script
#拉取分支
git clone https://github.com/{githubid}/SolidUI.git --branch dev
#根据 dev 生成本地 dev-fix 分支
git checkout -b dev-fix dev
#把本地 dev-fix 分支推到自己的仓库
git push origin dev-fix dev-fix
```

### 2.3 Issue 提交指引

- 如果您还不知道怎样向开源项目发起 PR，请参考[About issues](https://docs.github.com/en/github/managing-your-work-on-github/about-issues)
- Issue 名称，应一句话简单描述您的问题或建议；为了项目的国际化推广，请用英文，或中英文双语书写 issue
- 每个 Issue，请至少带上 label.参考:[issue #63](https://github.com/CloudOrc/SolidUI/issues/63)

### 2.4 Pull Request(PR) 提交指引

- 如果您还不知道怎样向开源项目发起 PR，请参考[About pull requests](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests)
- 无论是 Bug 修复，还是新功能开发，请将 PR 提交到 dev 分支

- PR 和提交名称遵循 `<type>(<scope>): <subject>` 原则，详情可以参考[Commit message 和 Change log 编写指南](https://github.com/CloudOrc/SolidUI-Doc/blob/main/zh_CN/%E5%BC%80%E5%8F%91%E6%96%87%E6%A1%A3/DevelopmentCommitMessage/README.md)
- 如果 PR 中包含新功能，理应将文档更新包含在本次 PR 中
- 如果本次 PR 尚未准备好合并，请在名称头部加上 [WIP] 前缀（WIP = work-in-progress）
- 所有提交到 dev-* 分支的提交至少需要经过一次 Review 才可以被合并

### 2.5 Review 标准

在贡献代码之前，可以了解一下什么样的提交在 Review 中是受欢迎的。简单来说，如果一项提交能带来尽可能多增益和尽可能少的副作用或风险，那它被合并的几率就越高，Review 的速度也会越快。风险大、价值低地提交是几乎不可能被合并的，并且有可能会被拒绝 Review。

#### 2.5.1 增益

- 修复导致 Bug 的主要原因
- 添加或修复一个大量用户亟需的功能或问题
- 简单有效
- 容易测试，有测试用例
- 减少复杂度以及代码量
- 经社区讨论过的、确定需要改进的问题

#### 2.5.2 副作用和风险

- 仅仅修复 Bug 的表面现象
- 引入复杂度高的新功能
- 为满足小众需求添加复杂度
- 改动稳定的现有 API 或语义
- 导致其他功能不能正常运行
- 添加大量依赖
- 随意改变依赖版本
- 一次性提交大量代码或改动

#### 2.5.3 Reviewer 注意事项

- 请使用建设性语气撰写评论
- 如果需要提交者进行修改，请明确说明完成此次 Pull Request 所需要修改的所有内容
- 如果某次 PR 在合并后发现带来了新问题，Reviewer 需要向 PR 作者联系并沟通解决问题；如果无法联系到 PR 作者，Reviewer 需要将此次 PR 进行还原

---

## 三、贡献进阶

### 3.1 关于 Committers（Collaborators）

#### 3.1.1 如何成为 Committer

如果您对 SolidUI 提过颇具价值的 PR 并且被合并，或是连续贡献超过半年，且至少主导过一次版本的发布，您可以通过官方微信群找到 SolidUI 项目的一个 PMC ，如果他愿意提名您为 committer，并愿意为您陈述您的贡献给所有 PMC 和 Committer，那么接下来会发起一次投票；PMC 和其他 Committers 将会一起投票决定是否允许您的加入，如果得到足够票数，您将成为 SolidUI 项目的 Committer。

#### 3.1.2 Committer 的权利

- 可以加入官方开发者微信群，参与讨论和制定 SolidUI 开发计划
- 可以对 Issue 进行管理，包括关闭、添加标签
- 可以创建和管理项目分支，dev 分支除外
- 可以对提交到 dev 分支的 PR 进行 Review
- 可以申请成为 Committee 成员

### 3.2 关于 Committee

#### 3.2.1 如何成为 Committee 成员

如果您是 SolidUI 项目的 Committer，并且您贡献的所有内容得到了其他 Committee 成员的认可，您可以申请成为 SolidUI Committee 成员，其他 Committee 成员将会一起投票决定是否允许您的加入，如果全票通过，您将成为 SolidUI Committee 成员。

#### 3.2.2 Committee 成员的权利

- 可以合并其他 Committers 和贡献者提交到 dev 分支的 PR
- 可以参与决定 SolidUI 项目的 roadmap 和发展方向
- 可以参与新版本发布
