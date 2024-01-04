# openEuler LLVM 平行宇宙计划·实习生参与指南

## 简介

「openEuler LLVM 平行宇宙计划」（后称 oE 平行宇宙）是 openEuler 社区的一个前瞻性项目，旨在探索使用 LLVM 工具链构建大部分乃至整个发行版的软件包的可能性。计划由社区 Compiler Sig 发起，RISC-V Sig 等积极响应，目前在软件所外有华为、统信、SUSE 等企业和科研院所多方参与。

**oERV 小队的实习生在其中主要承担修包类工作**（其中通常不包含软件版本升级），欢迎所有完成 `pretask` 获得正式实习资格的同学参与，部分挑战性工作后续也会作为 `hardwork` 发布。

## 前置步骤

- 获得正式实习资格
- 在实习生群中讲一声想要参与，由 staff 拉入 oE 平行宇宙的公开交流群以及同步小群
- 阅读群公告中的文档内容，了解构建工程位置、中间仓位置等基础信息

## 工作流和背给

- 工作流和 oERV 实习生指南中 `easywork` 章节中描述的大致相同，不同之处如下：
  - 修改在 OBS 个人仓验证通过后，应当先提交到中间仓 `parallel` 分支暂存。若此分支还未创建，请在同步小群中找 Staff 帮忙。
- oE 平行宇宙面向 x86_64, aarch64 以及 riscv64 三个架构，构建过程中三架构报错的类型可能相同也可能不同。
  - x86_64 和 aarch64 构建过程中出现的问题主要和切换编译器为 LLVM 有关
  - riscv64 在上述问题之外还有较小可能出现软件未有/未充分适配 RISC-V 架构相关的问题

> 对应软件包的构建可能已经被 disabled，可展开 `excluded/disabled results` 点击灰色的 `disabled` 链接查看先前构建 log.

- 如希望参照对应的 gcc 版本构建过程和 log，x86_64 和 aarch64 的对应软件包一般在开放原子 OBS 平台的[`openEuler:23.09`工程](https://build.openeuler.openatom.cn/project/show/openEuler:23.09)下。riscv64 的对应软件包一般在开放原子 OBS 平台的[`openEuler:23.09:RISC-V`工程](https://build.openeuler.openatom.cn/project/show/openEuler:23.09:RISC-V)下。
- 切换 llvm 编译器后常见的问题可以参考群内记录和群文件，解决方法还可以参考先前的 PR 等。

## 附注

- oE 平行宇宙为多方合作的社区项目，请各位同学在贡献时注意遵守开源社区规范和以及自身行为对软件所的公开影响。
