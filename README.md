# dsh-files

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
