# 🍅 番茄小说品鉴师 · fanqie-novel-critic

> 一个给书友用的 [Claude](https://claude.ai) / [Claude Code](https://docs.claude.com/claude-code) 技能（Skill）。
> 给一本番茄小说的**书名或链接**，自动抓取**前 3 章**，由四位「品鉴官」分别点评，帮你在跳坑前判断值不值得追。

番茄小说上 AI 水文、流水线套路文越来越多，偶尔才有精品。一本本点开试毒太累——
让 AI 帮你把**开局**拆开来看，像鉴酒一样出一份品鉴报告。

## 四位品鉴官

| 品鉴官 | 干什么 | 给分 |
|---|---|---|
| 🤖 **AI 鉴定师** | 判断是不是 AI 水文 / 流水线代写 | AI 嫌疑度（越低越好） |
| 🎭 **套路识别师** | 认出真千金假千金、追妻火葬场、系统流、赘婿逆袭等套路，判断新不新鲜 | 套路浓度（越低越好） |
| ✍️ **文风鉴定师** | 贴文风标签：拖沓 / 简洁 / 神秘 / 爽快……描述读起来的体感 | 文笔质感（越高越好） |
| 🎬 **开局鉴定师** | 评前 3 章悬念/钩子够不够强、值不值得追 | 追读指数（越高越好） |

最后 **主编** 综合给出「🏆 值得追 / 👍 可以追 / 😐 食之无味 / ⛔ 建议劝退」+ 雷点预警 + 适合人群。

示例报告见 [`examples/sample-report.md`](examples/sample-report.md)。

## 怎么用

装好后（见下），直接跟 Claude 说：

- `帮我品鉴一下番茄小说《末日全球海洋，勒索校花百万物资》`
- `这本书值不值得看：https://fanqienovel.com/page/7246248681131740175`
- `《书名》是不是 AI 写的？套路重不重？`

Claude 会自动打开番茄网页、抓前 3 章、跑完四位品鉴官、输出报告。

## 运行要求

- **首选（全自动）**：Claude 环境里接入了浏览器（[Claude in Chrome](https://claude.ai/chrome) 扩展 / claude-in-chrome）。
  这样只给个书名，剩下的抓取全自动完成。
  > 原理：番茄网页正文有字体加密，直接爬是乱码；但**真实浏览器渲染出来是明文**，
  > 所以本 skill 用浏览器渲染 + 截图读字，天然绕过加密。
- **兜底（无浏览器）**：没有浏览器时，把番茄**链接**发给 Claude（至少能读到书名/简介/标签），
  或自己**截图前 3 章** / **粘贴前 3 章文本**，四位品鉴官照样能工作。

## 安装

### 用在 Claude Code（命令行）

把这个仓库放到你的 skills 目录：

```bash
git clone https://github.com/violasi/fanqie-novel-critic.git ~/.claude/skills/fanqie-novel-critic
```

（或下载 zip 解压到 `~/.claude/skills/fanqie-novel-critic/`。）
重启 / 新开一个 Claude Code 会话，说「品鉴一下番茄小说《xxx》」即可触发。

### 分享给书友

把这个仓库链接发给书友，让 TA 按上面步骤 clone 到自己的 `~/.claude/skills/` 就行。
不想装的书友，也可以直接把 `SKILL.md` 的内容贴给 Claude，让它照着流程做。

## 目录结构

```
fanqie-novel-critic/
├── SKILL.md                  # 主编排：品鉴流程 + 四位品鉴官 + 报告模板
├── references/
│   ├── fetch-guide.md        # 抓取指南（实测的浏览器步骤 + 兜底方案）
│   ├── tropes.md             # 网文套路库（女频/男频/共通桥段 + 新鲜度）
│   ├── styles.md             # 文风词典 + 毒点信号
│   └── ai-tells.md           # AI 水文特征清单
├── examples/
│   └── sample-report.md      # 一份真实示例报告
├── README.md
└── LICENSE
```

## 免责声明

- 本工具仅抓取**公开可读的前几章**用于个人**品鉴/避雷**，不做整本下载、不传播、不商用。
- 品鉴是**主观参考意见**，不代表官方定论，也不代表本仓库作者观点。好不好看，最终以你自己读为准。
- 番茄网页结构随时可能变化，抓取步骤如失效欢迎提 Issue / PR。
- 与「番茄小说」官方无任何关联。

## License

[MIT](LICENSE)
