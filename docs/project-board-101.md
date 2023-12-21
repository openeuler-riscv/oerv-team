# openEuler RISC-V kanban 使用指南

更新日期: 2023-12-21

看版是为了更直观的看到有哪些任务，哪些任务被分配到哪个人了。默认会在 Default 页面以 Status 的状态分组显示。

## 各个 field 的介绍

### Status

 - Planning: 代表里面的 task 还在计划当中，随时可能会改变。
 - Help wanted: 代表这项 task 已经规划完成，处于无人认领的状态。
 - Todo: 代表有人认领这项 task，但还没开始工作。
 - In Progress: 代表有人认领这项 task，并且已经有一些进展了。
 - Done: 代表这项 task 已经结束。

### Priority

**请不要随便更改 Priority，如果后期更改了最好在 issue 内说明一下理由。**

 - P1: 代表即使人手十分不足的时候也要优先处理这个问题，通常是非常严重的问题，影响到了使用，无法临时提供简单 workaround，或者是紧急 task。
 - P2: 代表我们后续会着重去处理这个问题，但这个问题不会严重到影响使用，临时可提供 workaround。
 - P3: 代表我们会处理这个问题，但目前有更重要的事情要做。
 - P4: 代表我们对这个问题什么时候能解决没有一个肯定的答案。

### Team

这项 field 的存在是为了分清某 task 的 Assignee 是谁。

 - Dev: 开发组
 - Test: 测试组
 - Intern: 实习生

## 主 Table 使用说明

可以直接在 kanban 上添加 issue。点击 kanban 上的 `Add item`，即可创建一个 issue 草稿。想把这个 issue 草稿转换成完整 issue 的时候，可以单击刚创建的 issue 前方的下拉栏，然后选择 `Convert to issue`，选择 `oerv-team`。不要忘记详细在 issue 内写明 task 相关的说明。

当自己想接受一个 task 的时候，需要修改 `Status` 为 `Todo`，并根据自己在什么 Team 来选择 `Team`。`Label` 同时也要将 `Unassigned` 更改成 `Assigned`，并在 `Assignee` 选择自己。后续根据情况再修改 `Status`。

如果放弃了一项 task，请务必更改对应的 `Label` 从 `Assigned` 换成 `Unassigned`，`Status` 为 `Help wanted`，并清空 `Team`。**再次提醒，请不要乱更改 `Priority`，如果后期更改了最好在 issue 内说明一下理由。**

## Timeline View 使用说明

可以在这个页面设置 task 的 `Start Date` 和 `End Date`。找到对应的 issue 之后，在后面选择一个开始日期，然后拖动长方形末尾即可设置结束日期。

默认开启了 Milestone 的 `Marker`，可以显示 Milestone 的时间节点。在 `oerv-team` 这个项目内创建带日期的 `Milestone`（例如 openEuler 24.03 LTS GA 日期为 2024-03-31）后，会自动显示在这个 Timeline 上。

> 注意，如果要使用 Milestone 功能，请务必至少一个 issue 到你想展示的 Milestone 内，否则 GitHub 是不会显示空 Milestone 的。

## FAQ

### Q: 我是 Intern，我看不到这个看版？

A: 在完成 pretask 之后，就会被邀请进入了，进入之后就可以看到了。
