# Aigis Desktop Pet / 埃吉斯桌宠

一个用于 ChatGPT 桌面应用 Codex/Pets 功能的非官方 Q 版埃吉斯桌宠。

- 空闲时站在原地，偶尔眨眼
- 执行任务时先朝左舞动双手，再朝右舞动双手
- 包含 9 个行为动画状态
- 使用 Sprite Sheet v2（`1536 × 2288`）
- 保留并公开 16 个方向的视线素材

![空闲动画](previews/states/idle.gif)

![执行任务动画](previews/states/working-dance.gif)

## 16 方向视线说明

完整的 16 方向视线帧同时保存在：

- 安装用 v2 图集的最后两行
- [`source-assets/gaze-directions/`](source-assets/gaze-directions/) 中的 16 张透明 PNG
- [`previews/look-directions.png`](previews/look-directions.png) 总览图

> **16 方向素材不等于普通鼠标视线跟随。**
>
> 当前项目不包含系统级鼠标监听，也没有修改 ChatGPT/Codex 客户端。因此，埃吉斯不会跟随普通桌面鼠标持续转动视线。是否调用这些方向帧由宿主客户端提供的交互目标决定；这些素材仍保留用于客户端支持的场景和后续开发。

## 动画内容

v2 图集包含 9 个行为动画行：

1. `idle`：空闲、偶尔眨眼
2. `running-right`：向右移动
3. `running-left`：向左移动
4. `waving`：挥手
5. `jumping`：跳跃
6. `failed`：失败/受阻
7. `waiting`：等待输入
8. `running`：执行任务时左右舞动
9. `review`：检查/完成提示

另有两行共 16 帧视线方向素材。所有状态可查看 [`previews/all-states.png`](previews/all-states.png) 和 [`previews/states/`](previews/states/)。

## 下载

请从 [GitHub Releases](https://github.com/JiazheWei/Aigis-Desktop/releases) 下载最新的：

`aigis-codex-pet-v1.0.0.zip`

Release ZIP 是安装包；不要把整个 GitHub 仓库复制到 Pets 目录。

## 安装方法一：交给 Codex 安装（推荐）

1. 下载 Release 中的 ZIP。
2. 在本机 ChatGPT/Codex 桌面应用中打开一个本地 Codex 对话。
3. 把 ZIP 拖入对话，并发送下面的提示词：

```text
请将附件 ZIP 安装为本机 ChatGPT/Codex 桌面应用的自定义桌宠。

要求：
1. 解压并检查文件结构。
2. 将 chibi-aigis-baby-dance 文件夹复制到本机的 Codex pets 目录。
3. 不要修改其他 Codex 设置，也不要覆盖无关桌宠。
4. 确认 pet.json 中的 spriteVersionNumber 为 2。
5. 确认 spritesheet.webp 的尺寸为 1536×2288。
6. 确保没有产生重复嵌套目录。
7. 完成后告诉我如何在 Settings > Pets 中刷新并启用它。
```

安装完成后，进入 `Settings > Pets`，点击 `Refresh`，选择“Q版埃吉斯”。输入 `/pet` 可以显示或隐藏桌宠。

## 安装方法二：手动安装

先解压 ZIP。正确的安装结果应为：

```text
~/.codex/pets/chibi-aigis-baby-dance/
├── pet.json
└── spritesheet.webp
```

### macOS / Linux

在解压目录中运行：

```bash
mkdir -p "$HOME/.codex/pets"
cp -R "./chibi-aigis-baby-dance" "$HOME/.codex/pets/"
```

### Windows PowerShell

在解压目录中运行：

```powershell
New-Item -ItemType Directory -Force "$HOME\.codex\pets"
Copy-Item -Recurse -Force ".\chibi-aigis-baby-dance" "$HOME\.codex\pets\"
```

随后打开 `Settings > Pets`，点击 `Refresh` 并选择“Q版埃吉斯”。

请避免产生重复目录：

```text
~/.codex/pets/chibi-aigis-baby-dance/chibi-aigis-baby-dance/
```

## 兼容性

- 面向 ChatGPT 桌面应用中的本地自定义 Pets 功能。
- 使用 Sprite Sheet v2；安装图集为透明 lossless WebP，尺寸 `1536 × 2288`。
- 已在作者当前使用的 macOS 桌面版本上验证。
- 系统启用“减少动态效果”时，宠物会使用静态帧。
- 官方网页端 `Upload pet` 当前公布的是另一套上传规格；本项目的 v2 包主要用于桌面本地安装。
- 选择桌宠只会改变显示形象，不会改变 Codex 执行任务的方式。

官方说明：

- [OpenAI Pets documentation](https://learn.chatgpt.com/docs/pets)
- [Pet install deep-link reference](https://learn.chatgpt.com/docs/reference/commands#pets)

## 仓库结构

```text
pet/                     可直接安装的运行文件
source-assets/           无损总图与 16 方向独立素材
previews/                状态、动画与方向预览
RELEASE_NOTES.md         v1.0.0 发布说明
NOTICE.md                权利与非官方声明
```

## English summary

This is an unofficial, fan-made Aigis desktop pet for the ChatGPT desktop app's Codex/Pets feature. It idles with an occasional blink and performs a left-to-right hand dance while a task is running.

The v2 sprite sheet and source assets include all 16 gaze-direction frames, but this package does **not** globally track the ordinary system mouse cursor. Download the Release ZIP, then either give it to a local Codex chat for installation or copy the pet folder into `~/.codex/pets/`.

## 权利说明

这是一个非官方、非商业性质的同人项目。角色美术不以 MIT 或其他开源软件许可证授权。使用或再分发前请阅读 [NOTICE.md](NOTICE.md)。
