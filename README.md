# dsh-files

> 本仓目前**只有 vk 版**：左栏「文件」Tab 与右栏「打开本机文件」标签的位置都由 [dsh-vk-suite](https://github.com/Ln1m/dsh-vk-suite)（契约 + 骨架）提供，需先装骨架。
> **两个版本模型里推荐 vk 版**：左栏 Tab 切换（会话 / 文件 / 任务 / 工具）与右栏、设置的位置都在骨架里，只有 vk 版装得进这些位置。

DSH Web 的左栏文件家族，两个包一个仓。

| 包 | 作用 |
|---|---|
| `dsh-files-tree` | 左栏「文件」Tab：文件树 + 应用内目录浏览器 + 最近打开 / 文件列表；输入区 `@` 引用也在这个包里 |
| `dsh-files-open` | 右栏「打开本机文件」标签（可以只装它） |

两个包都要装框架（`dsh-vk-contract` + `dsh-vk-layout`）才会出现位置：没有骨架，它们注册的槽没人声明，页面上就什么都不多。

## 装

```powershell
dsh plugin --profile web add file:<dsh-vk-suite 路径>/dsh-vk-contract
dsh plugin --profile web add file:<dsh-vk-suite 路径>/dsh-vk-layout
dsh plugin --profile web add file:<本仓库>/dsh-files-tree
dsh plugin --profile web add file:<本仓库>/dsh-files-open
```

装完重启 DSH。左栏多一个「文件」Tab，右栏多一个「打开本机文件」标签。

## 推荐搭配 / 可能冲突

- **推荐和骨架一起装**：[dsh-vk-suite](https://github.com/Ln1m/dsh-vk-suite)（`dsh-vk-contract` + `dsh-vk-layout`）里的**左栏 Tab 切换**（会话 / 文件 / 任务 / 工具）就是文件树所在的位置——只装本包不会出现左栏「文件」入口。
- 右栏「打开本机文件」标签的正文同样由骨架登记：没装骨架时这个标签标题在、内容只剩官方兜底文案。
- **可能冲突**：本包有意**顶替官方的 `files` 标签类型**（这样「新标签页」列表里不会出现官方那条重复项），并在 `conversation.input.left` 挂输入区 `@` 引用。同样注册 `files` 类型、或往 `conversation.input.left` 同优先级注册的插件与本包互斥：先注册的赢，后注册的抛错被吞掉，表现为其中一方整块不出现。
- 与「三栏布局」类插件叠加时，左栏形状以优先级最高的那一个为准。

## 配置

| 项 | 位置 | 默认 |
|---|---|---|
| 落地页常用根 | `dsh-files-tree/lib/client.js` 的 `HOME_DIRS` | `[]`；要固定展示自己的目录，在这里补条目 |
| 桌面快捷入口 | 同文件 `DESKTOP_HINT` | 空；填自己的桌面路径才显示 |

## 环境变量

| 变量 | 默认 | 说明 |
|---|---|---|
| `DSH_ROOT` | `~/DeepSeek_harness` | DSH 安装根；「agent 侧目录」由它派生 |

## License

MIT
