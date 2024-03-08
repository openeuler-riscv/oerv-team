# openEuler 源码仓 PR 合并指南

更新日期: 2024-03-07

## 前言

向 openEuler 社区作出贡献有许多种方法，对源码仓提出 PR 是其中之一。本文档将对如何向 src-openeuler 下的源码仓作出贡献做一个简单的指北。

在此之前，我们首先要知道 openEuler 每发布一个版本都包括哪些软件包。通常来讲，openEuler 在不同的大版本都会在各个源码包内创建一次以版本命名的分支。例如 `openEuler-23.09` 分支和 `openEuler-24.03-LTS` 分支。

而 LTS 版本又会有 SP1、SP2 这样的版本，所以你会看到 `openEuler-22.03-LTS-SP1`、`openEuler-22.03-LTS-SP3` 这样的分支。

至于 LTS 带有 Next 的分支，则是为了下一个 LTS 版本准备的。例如在 `openEuler-22.03-LTS` 发布的时候，会同时创建 `openEuler-22.03-LTS-Next`，这样后续的 SP1 版本将直接从 `openEuler-22.03-LTS-Next` 拉取，而不是 `master`。

`master` 分支为 openEuler 源码仓最前沿的分支。dailybuild 镜像会基于这个镜像制作。

此时你可能会问，我贡献的 xxx 包没有任何这些分支，只有 `master` 分支！这通常是本包没有被纳入 [Everything (Mainline)](https://eulermaker.compass-ci.openeuler.openatom.cn/project/overview?osProject=openEuler-master:everything) 或 [Epol](https://eulermaker.compass-ci.openeuler.openatom.cn/project/overview?osProject=openEuler-master:epol)，仅存在于 [Factory](https://eulermaker.compass-ci.openeuler.openatom.cn/project/overview?osProject=openEuler-master:factory) 内。这也意味着，xxx 包将不会在任何 openEuler 版本内出现。如果想改变这个情况，需要去 [release-management](https://gitee.com/openeuler/release-management) 发起 PR 修改，这不是本次讨论的对象。

## 那我该如何贡献呢？

通常情况下，只需要提交你的 PR 至 `master` 分支即可。针对 openEuler 特定版本的包升级应在分支冻结之前合并。

## 听君一席话，如听一席话

不要急！我来给你举两个例子。

### 遇到创新版本该如何做

> openEuler 23.09 的发布已经拉上日程，并且此时已经从 `master` 拉出 `openEuler-23.09` 的分支，我需要修复某个包。

首先，fork 对应的仓库，然后将你的更改提交。之后，提交针对 `master` 分支的 PR。

此时可以看到门禁的提示：使用 `/sync <branch>` 可以将当前 PR 修改同步到其它分支，此时我当然想同步了，所以在下方输入 `/sync openEuler-23.09`。在本 PR 合并之后，openeuler-sync-bot 就会自动开启针对 `openEuler-23.09` 分支的同步 PR。

### 遇到 LTS 版本该如何做

> openEuler 24.03 LTS 的发布已经拉上日程，并且此时已经从 `master` 拉出 `openEuler-24.03-LTS` 和 `openEuler-24.03-LTS-Next` 我需要修复某个包。

同样的，fork 对应的仓库，然后将你的更改提交。之后，提交针对 `master` 分支的 PR。

此时可以看到门禁的提示：使用 `/sync <branch>` 可以将当前 PR 修改同步到其它分支，此时我当然想同步了，所以在下方输入 `/sync openEuler-24.03-LTS openEuler-24.03-LTS-Next`。在本 PR 合并之后，openeuler-sync-bot 就会自动开启针对 `openEuler-24.03-LTS` 和 `openEuler-24.03-LTS-Next` 分支的两个同步 PR。

为什么要同步到两个呢？因为后续的 LTS 版本会从 LTS-Next 分支拉取，我们需要确保后面都要应用到这个更改。

### Q & A

#### 有没有例子可以看？

有。[例子 PR](https://gitee.com/src-openeuler/deepin-desktop-base/pulls/41) & [通过 bot 创建的合并 PR](https://gitee.com/src-openeuler/deepin-desktop-base/pulls/42)。

#### bot 在 PR 合并之后显示 "同步失败：请手动创建 PR 进行同步，我们会继续完善分支之间同步操作，尽量避免同步失败的情况"

此时需要手动开同步 PR，在对应的分支自己修改之后提交 PR 即可。

#### bot 开的 PR 也需要等待 maintainer 合入吗？

是。

#### 假设我有一个修改要应用到每个 22.03 LTS 的版本，那我是不是都要同步一次？

是。目前来说 22.03 有 5 个分支：LTS、LTS-SP1、LTS-SP2、LTS-SP3、LTS-Next。也就是说无论是自己提还是 bot 辅助提，总用需要 5 个 PR，每个版本 1 个。

#### 如果我在社区还没有定新版本的时候提交修改，那我是不是只需要管 `master` 分支就可以了？

是。

#### 你在上面说了分支冻结？

可以在 [release-management](https://gitee.com/openeuler/release-management) repo 里面根据不同版本看 release plan。在分支冻结之前，bug fix 和版本升级都可以。在分支冻结之后，只允许 bug fix，而不允许版本升级。不过最好在分支冻结之前做完所有的工作嘛。
