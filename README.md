# campus-operations-kb · 校园运营知识库

一套用 MkDocs 搭建的校园运营知识库：把"重邮学长"账号在**驾校代理、校园卡、二手书、抖音选题、复习资料、新生指南**六条业务线上的话术、流程、风险与数据，整理成可搜索、可离线分发的静态文档站。

---

## 项目简介

这是一个**个人向的校园运营知识库**，服务于一名重庆邮电大学在读学生运营的抖音账号（"重邮学长 · 新生干货"）及其线上副业：抖音内容引流 → 私信搭桥 → 驾校代理 / 二手书 / 校园卡成交。

它解决的问题是：运营过程中积累的话术、流程、合规红线散落在聊天记录、PDF 手册和零散笔记里，用时找不到、带新人讲不清。项目把这些内容拆成**一篇一场景的"知识卡片"**，统一放进 MkDocs 站点，支持中文全文搜索，并能构建成可直接分发的离线站点。

需要说明的是：这不是教学项目或比赛作品，仓库中的内容带有明确的**业务内部属性**（含线下合作方名称、报价口径、销售话术与风险处置口径），文档本身也反复强调合规底线。

---

## 功能特性

- **三套独立站点，面向三类读者**：内部完整版（`knowledge-base`）、团队共享版（`knowledge-base-team`）、对外新生版（`knowledge-base-freshman`），各自有独立的 `mkdocs.yml` 与 `docs/`，互不干扰。
- **六大业务板块**：驾校代理、校园卡、二手书、抖音选题、复习资料、新生指南，每块都有总览页 + 子分类导航 + 高频速查。
- **卡片化写作**：每篇文档以 YAML front matter 标注 `tags` / `keywords`，正文按「场景 → 话术 → 要点 → 禁忌」组织，便于现场即查即用。
- **中文全文搜索**：MkDocs search 插件配 `lang: zh` 与自定义分隔符正则，中文关键词可直接命中。
- **深色 / 浅色双主题**：基于 mkdocs-material 的 indigo（内部版）/ teal（新生版）配色与切换按钮。
- **离线分发能力**：新生版站点开启 `use_directory_urls: false` 且 `font: false`，改用系统字体栈，产物可直接双击 `index.html` 打开，也已打包为 `重邮新生干货站.zip` 供线下分发。
- **资料双向可追溯**：`原始材料/` 存放素材原件，`提取文本/` 存放从 PDF/DOCX 提取的纯文本，`最终输出/` 存放业务整理成稿，再由 `docs/` 拆成知识卡片。

---

## 目录结构

```text
campus-operations-kb/
├── .gitignore
├── knowledge-base/                      # 站点一：内部完整版《重邮学长运营知识库》
│   ├── mkdocs.yml
│   ├── docs/                            # 70 篇 Markdown
│   │   ├── index.md                     # 六大板块总览 + 高频速查表 + 更新日志
│   │   ├── jiashu/                      # 驾校代理（18 篇）
│   │   │   ├── index.md
│   │   │   ├── huashu/                  # 话术 001~007
│   │   │   ├── liucheng/                # 流程 001~003
│   │   │   ├── fengxian/                # 风险 001~005
│   │   │   ├── kangju/                  # 抗拒处理 001
│   │   │   └── shuju/                   # 数据速查 001
│   │   ├── xiaoyuanka/                  # 校园卡（15 篇）
│   │   │   ├── index.md
│   │   │   ├── huashu/                  # 话术 001~009
│   │   │   ├── liucheng/                # 流程 001~004
│   │   │   ├── fengxian/                # 合规底线 001
│   │   │   └── kangju/                  # 预留空目录
│   │   ├── ershushu/                    # 二手书（10 篇：index + huashu 5 + liucheng 3 + fengxian 1）
│   │   ├── douyin/                      # 抖音选题（19 篇：index + 策略 4 + 选题卡片 14）
│   │   ├── fuxiziliao/                  # 复习资料（3 篇：index + mulu 1 + celue 1）
│   │   ├── xinsheng/                    # 新生指南（4 篇：index + zhinan 3）
│   │   └── stylesheets/extra.css        # 侧边栏滚动 / 搜索框吸顶等修正
│   └── site/                            # 构建产物（.gitignore 忽略）
├── knowledge-base-team/                 # 站点二：团队共享版《校园运营团队知识库》
│   ├── mkdocs.yml                       # 与站点一导航结构一致，配色/说明文案略有差异
│   ├── docs/                            # 70 篇 Markdown
│   └── site/
├── knowledge-base-freshman/             # 站点三：对外新生版《重邮新生干货站》
│   ├── mkdocs.yml                       # use_directory_urls: false、font: false（离线友好）
│   ├── docs/                            # 15 篇 Markdown
│   │   ├── index.md
│   │   ├── gonglve/                     # 校园攻略 8 篇（index + 001~007）
│   │   ├── xinsheng/                    # 入学指南（index + zhinan 001~003）
│   │   ├── kaoshi/                      # 复习资料（index + 各科目资料清单）
│   │   └── stylesheets/extra.css        # 离线字体栈 + 侧边栏滚动修正
│   └── site/
├── 提取文本/                            # 11 个 .txt：从原始 PDF/DOCX 提取的纯文本
├── 最终输出/                            # 6 篇业务整理 Markdown + 2 个独立 HTML 报告
└── 原始材料/                            # 四批素材原件（约 951MB，已 .gitignore，不入库）

重邮新生干货站.zip                        # 站点三的离线包（本地文件，已被 *.zip 规则忽略）
```

> `site/`、`原始材料/`、`*.zip` 均在 `.gitignore` 中排除，克隆仓库后需要自行放置素材并重新构建站点。

---

## 快速开始

### 1. 环境准备

需要 Python 3（本地实测 Python 3.12.10）。项目**没有** `requirements.txt`，注意 `pymdownx.*` 扩展由 mkdocs-material 的依赖 pymdown-extensions 提供。

```bash
python -m pip install mkdocs mkdocs-material
```

### 2. 本地预览

三个站点的配置文件都在各自子目录，**必须用 `-f` 指定**（仓库根目录没有 `mkdocs.yml`）：

```bash
# 内部完整版
mkdocs serve -f knowledge-base/mkdocs.yml

# 团队共享版
mkdocs serve -f knowledge-base-team/mkdocs.yml

# 对外新生版
mkdocs serve -f knowledge-base-freshman/mkdocs.yml
```

默认监听 `http://127.0.0.1:8000`，改端口加 `-a 127.0.0.1:8001`。

### 3. 构建静态站点

```bash
mkdocs build -f knowledge-base/mkdocs.yml
mkdocs build -f knowledge-base-team/mkdocs.yml
mkdocs build -f knowledge-base-freshman/mkdocs.yml
```

产物默认写入各自目录下的 `site/`。本地以 Python 3.12.10 + MkDocs 1.6.1 + mkdocs-material 9.7.7 实测，三个站点均构建成功。

### 4. 构建离线包（新生版）

新生版使用扁平化 URL（`xxx.html` 而非 `xxx/index.html`），构建后整个 `site/` 可直接拷贝或压缩分发，双击 `index.html` 即可离线浏览：

```powershell
mkdocs build -f knowledge-base-freshman/mkdocs.yml
Compress-Archive -Path knowledge-base-freshman/site/* -DestinationPath 重邮新生干货站.zip -Force
```

### 5. 新增一张知识卡片

1. 在对应板块的子目录新建 Markdown，例如 `knowledge-base/docs/jiashu/huashu/008-新场景.md`；
2. 文件头补上元数据，正文按卡片结构书写：

```markdown
---
tags: [驾校, 话术, 高频]
keywords: [关键词1, 关键词2]
---

# 卡片标题

## 场景
## 话术
## 要点
## 禁忌
```

3. 在所在板块的 `index.md` 导航列表里补一行链接；
4. 若要出现在左侧侧边栏，还需要在 `mkdocs.yml` 的 `nav:` 中登记该文件；
5. 改完执行 `mkdocs build`（或 `mkdocs serve` 热重载）验证。

---

## 内容组织

### 六大板块（内部完整版 / 团队共享版）

| 板块 | 目录 | 内容要点 |
|------|------|---------|
| 🚗 驾校代理 | `docs/jiashu/` | 极简引流四步法、点对点聊天四步法、对账结算流程；价格/隐形消费/团报/投诉等话术；结算、口碑、人设、业务冲突风险与 7 条合规红线；九城驾校关键数据速查 |
| 📱 校园卡 | `docs/xiaoyuanka/` | 移动 59 元主推 + 电信 29 元备选；首次对话、过渡切入、三家对比、家长沟通、售后等 9 类话术；销售全流程与出卡操作；多平台引流策略；合规底线 7 条 |
| 📚 二手书 | `docs/ershushu/` | 收书端 4 步 + 卖书端 5 步；视频软植入、私信问书、议价、缺货、书况争议话术；年度运营节奏与库存管理 |
| 🎬 抖音选题 | `docs/douyin/` | 三层漏斗策略（泛吸引 70% / 软种草 25% / 促转化 5%）、发布时间节奏、发布 SOP 清单、关键数据指标；14 条选题卡片（含视频结构、植入方式、发布时间） |
| 📖 复习资料 | `docs/fuxiziliao/` | 各科目资料清单（高数、C 语言、线代、近现代史、马原、微观经济学等）与资料销售策略 |
| 🎓 新生指南 | `docs/xinsheng/` | 选课避坑、志愿与劳动时长要求、挂 VPN 教程，兼作抖音/小红书选题的素材库 |

### 三套站点的差异

| 站点 | 站名 | 定位 | 板块 | 导航特性 |
|------|------|------|------|---------|
| `knowledge-base` | 重邮学长运营知识库 | 内部完整版，含合作方口径与结算细节 | 6 大板块，70 篇 | `navigation.sections` + `navigation.expand`，indigo 配色 |
| `knowledge-base-team` | 校园运营团队知识库 | 给团队成员共享，弱化个人化表述 | 6 大板块，70 篇 | `navigation.sections`，indigo 配色 |
| `knowledge-base-freshman` | 重邮新生干货站 | 对外发布，只讲干货、不带业务推广 | 3 大板块（校园攻略 / 入学指南 / 复习资料），15 篇 | teal 配色、扁平化 URL、系统字体、可离线打开 |

---

## 技术栈

- **静态站点生成**：[MkDocs](https://www.mkdocs.org/) 1.6.1
- **主题**：[mkdocs-material](https://squidfunk.github.io/mkdocs-material/) 9.7.7（`language: zh`，深浅色双 palette）
- **搜索**：MkDocs 内置 `search` 插件，`lang: zh` + 自定义中英文分隔符正则
- **Markdown 扩展**：`admonition`、`tables`、`toc(permalink)`、`pymdownx.highlight`、`pymdownx.superfences`
- **自定义样式**：`docs/stylesheets/extra.css`（侧边栏滚动、搜索框吸顶、离线字体栈）
- **素材处理**：PDF → 文本使用 `pdftotext -layout`；DOCX 内容提取为纯文本后归档到 `提取文本/`
- **运行环境**：Python 3.12（作者本机）

---

## 文档索引

### 站点入口页

| 文件 | 说明 |
|------|------|
| `knowledge-base/docs/index.md` | 六大板块速览 + 高频场景速查表 + 更新日志 |
| `knowledge-base-team/docs/index.md` | 团队共享版首页（内容与上一份基本一致） |
| `knowledge-base-freshman/docs/index.md` | 新生站首页：三大板块 + 快速入口 |

### 各板块总览

`knowledge-base/docs/jiashu/index.md`、`knowledge-base/docs/xiaoyuanka/index.md`、`knowledge-base/docs/ershushu/index.md`、`knowledge-base/docs/douyin/index.md`、`knowledge-base/docs/fuxiziliao/index.md`、`knowledge-base/docs/xinsheng/index.md`

### 业务整理成稿（`最终输出/`）

| 文件 | 说明 |
|------|------|
| `最终输出/驾校代理合作完整总结.md` | 九城驾校合作模式对比、定价体系、提成与结算、风险清单 |
| `最终输出/驾校代理业务整理.md` | 驾校业务线整理稿 |
| `最终输出/校园卡业务整理.md` | 校园卡产品详情、销售流程与话术整理稿 |
| `最终输出/二手书业务整理.md` | 二手书业务定位、与驾校/校园卡的差异对比、运营节奏 |
| `最终输出/抖音选题与内容规划.md` | 三层漏斗策略与完整选题规划（另有同名单文件 HTML 版） |
| `最终输出/最新材料整理总结.md` | 7.14 批次材料的内容概览与「与原业务的关联/需调整点」 |
| `最终输出/抖音选题与内容规划.html`、`最终输出/驾校代理合作总结.html` | 自带样式的单文件 HTML 报告，可直接浏览器打开 |

### 素材文本（`提取文本/`）

| 文件 | 来源 |
|------|------|
| `校园线上营销技巧与话术_重庆.txt` | 校园线上营销方法论：引流建群、聊天节奏、抗拒处理、合规底线 |
| `manual_js.txt`、`agent_manual.txt`、`agent_manual_raw.txt` | 九城驾校代理手册（含 PDF 直出与清洗版） |
| `tips_js.txt`、`recruitment_tips.txt` | 招生 / 沟通技巧类材料 |
| `chat_records.txt`、`chat_js.txt` | 聊天记录与话术片段 |
| `22b0f9e67c588f3d5b5b64257edd0cf1.txt` | 校园地图册文案（校园风景动线） |
| `88dddf97aa06664ceb67b0016d109188.txt` | 食宿条件揭秘文案（7 个食堂 + 宿舍） |
| `fe8c327893b61e34199a990b50a8a40a.txt` | 校园活动合集文案 |

---

## 备注 / 已知问题

- **仓库未包含开源许可证**，也没有 CI 配置、依赖清单（`requirements.txt`）和测试脚本；README 中的构建命令均为本地实测可用的手工步骤。
- **内容带有业务属性**：文档中的驾校名称、报价口径、话术与"甩锅/零售后"等表述属于运营方内部口径；若你只是参考其知识库组织方式，请自行判断内容适用性，并注意各平台规则与相关合规要求（文档自身也列出了 7 条合规底线）。
- **`原始材料/` 未入库**（约 951MB，被 `.gitignore` 排除），因此克隆后无法复现 `提取文本/` 的全部来源，只能依据已提取的文本；其中 `agent_manual.txt`、`recruitment_tips.txt` 等文件为 **GBK 编码**，按 UTF-8 读取会报错，需用 GBK/ANSI 方式打开。
- **站点一与站点二高度重复**：`knowledge-base/docs` 与 `knowledge-base-team/docs` 内容绝大多数一致（仅首页文案、个别卡片和导航特性有差异），修改时需要**手工同步两处**，否则内容会漂移。
- **构建产物与本地改动**：`site/` 为 `.gitignore` 排除的构建产物；此外 `knowledge-base-freshman/mkdocs.yml` 与 `knowledge-base-freshman/docs/stylesheets/extra.css` 在本地存在尚未提交的修改（离线模式相关）。
- **小瑕疵**：首页与抖音板块总览写"12 条核心选题"，实际选题卡片为 14 条（`选题-001` ~ `选题-014`）；`docs/xiaoyuanka/kangju/` 是预留但为空的目录，未登记进 `nav`。
- **工具链提示**：mkdocs-material 9.7.x 在构建时会输出一段关于 MkDocs 2.0 的提示信息，不影响当前构建（实测三个站点 `exit code 0`）；若日后升级到 MkDocs 2.x，主题系统需要重新适配。
- **中文搜索**：`search` 插件使用自定义分隔符正则（含中英文标点），若新增内容后搜索词切分异常，可优先检查 `mkdocs.yml` 中的 `separator` 配置。
