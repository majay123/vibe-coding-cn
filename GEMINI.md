# GEMINI.md - 项目上下文文档 (Project Context Document)

## 项目概述 (Project Overview)

`vibe-coding-cn` 项目旨在提供一个通过与 AI 结对编程实现“将想法变为现实”的终极工作流程。它强调“规划驱动”和“模块化”的核心理念，旨在避免 AI 失控导致的项目混乱。该项目不仅仅是一个代码库，更是一个全面的 AI 结对编程指南和工具集，涵盖了从项目构思、技术选型、实施规划到具体开发、调试和扩展的全过程。

**核心理念:** 规划是核心，通过结构化、模块化的方式引导 AI，确保项目可控、可维护。

## 技术栈 (Technology Stack)

本项目主要的技术栈和相关工具包括：

*   **核心语言:** Python (用于 `prompts-library` 工具和备份脚本)
*   **CLI 交互:** `rich`, `InquirerPy` (用于 `prompts-library` 提供友好的命令行界面)
*   **数据处理:** `pandas`, `openpyxl` (用于 `prompts-library` 处理 Excel 文件)
*   **配置管理:** `PyYAML`, `python-dotenv` (用于配置和环境变量)
*   **文档规范:** `markdownlint-cli` (用于 `Makefile` 中的 `lint` 任务，确保 Markdown 文档质量)
*   **AI 辅助工具集成:** `auggie-mcp` (用于增强 AI 在代码库中的检索和分析能力，支持 Claude Code 和 Codex)
*   **版本控制:** Git
*   **自动化:** Makefile (用于定义项目自动化任务，如 lint)
*   **操作系统:** 兼容 Linux (备份脚本中的路径处理)

## 主要功能与工作流程 (Key Features & Workflow)

1.  **AI 提示词管理 (`prompts-library`):**
    *   提供 Python 工具 (`main.py`, `scripts/start_convert.py`)，用于在 Excel 工作簿 (`prompt_excel/`) 和 Markdown 文档 (`prompt_docs/`) 之间进行提示词的相互转换。
    *   支持交互式选择和非交互式命令行操作，方便自动化处理。
    *   输出文件会带有时间戳，便于管理和回溯。

2.  **丰富的 AI 提示词库 (`prompts/`):**
    *   `coding_prompts/`: 专注于编程和代码生成的提示词，包含用于项目上下文文档生成等工程化提示词。
    *   `system_prompts/`: 包含用于设定 AI 行为和思维框架的系统级提示词，如 `CLAUDE.md` 系列。
    *   `user_prompts/`: 存放用户自定义或常用的提示词。
    *   `assistant_prompts/`: 辅助类提示词 (虽然目录存在但未在 `README.md` 中详细说明)。

3.  **项目备份工具 (`backups/`):**
    *   `快速备份.py` 是一个 Python 脚本，能根据 `.gitignore` 规则智能地打包项目文件为 `.tar.gz` 格式。
    *   通过 `一键备份.sh` 脚本可快速执行备份操作。

4.  **AI 结对编程工作流指南:**
    *   `README.md` 详细阐述了“规划驱动 + 上下文固定 + AI 结对执行”的核心工作流。
    *   提供了 3 分钟 CLI 演示剧本，指导用户如何利用项目中的提示词进行需求理解、计划生成和代码实现。
    *   强调了 AI 工具（如 Claude Code, Codex CLI）的使用技巧和最佳实践。

5.  **知识库与文档 (`documents/`):**
    *   包含代码组织、开发经验、系统提示词构建原则、项目架构模板等各类文档。
    *   `auggie-mcp配置文档.md` 提供了配置 `auggie-mcp` 的详细指引，以提升 AI 的代码理解能力。

## 开发与自动化 (Development & Automation)

*   **linting:** 使用 `Makefile` 中的 `lint` 任务，通过 `markdownlint-cli` 确保 Markdown 文档的格式和规范。
*   **构建/测试:** `Makefile` 中包含 `build` 和 `test` 的占位符，表明未来可能集成更完善的自动化构建和测试流程。目前这些可能依赖于具体的 Python 脚本或其他外部工具。
*   **依赖管理:** Python 依赖通过 `prompts/prompts-library/requirements.txt` 进行管理。

## 贡献与规范 (Contribution & Conventions)

*   项目欢迎各种形式的贡献，并提供了 `CONTRIBUTING.md` 和 `CODE_OF_CONDUCT.md` 作为贡献者指南和行为准则。
*   文档质量和规范性受到重视，通过 `markdownlint` 进行检查。

## 文件结构 (File Structure)

```
.
├── CODE_OF_CONDUCT.md           # 社区行为准则，规范贡献者行为。
├── CONTRIBUTING.md              # 贡献指南，说明如何为本项目做出贡献。
├── LICENSE                      # 开源许可证文件。
├── Makefile                     # 项目自动化脚本，用于代码检查、构建等。
├── README.md                    # 项目主文档，包含项目概览、使用指南、资源链接等。
├── .gitignore                   # Git 忽略文件。
│
├── documents/                   # 存放各类说明文档、经验总结和配置详细说明。
│   ├── auggie-mcp配置文档.md      # Augment 上下文引擎配置文档。
│   ├── 代码组织.md                # 代码组织与结构相关文档。
│   └── ... (其他文档)
│
├── prompts/                     # 集中存放所有类型的 AI 提示词。
│   ├── coding_prompts/          # 专门用于编程和代码生成相关的提示词集合。
│   │   ├── (1,1)_#_📘_项目上下文文档生成_·_工程化_Prompt（专业优化版）.md # 具体编程提示词示例。
│   │   └── ... (其他具体编程提示词文件)
│   │
│   ├── prompts-library/         # 提示词库管理工具。
│   │   ├── main.py              # 提示词库管理工具主入口，处理 Excel 与 Markdown 转换。
│   │   ├── requirements.txt     # Python 依赖列表。
│   │   ├── scripts/             # 包含 Excel 与 Markdown 互转脚本和配置。
│   │   └── ... (其他 prompts-library 内部文件)
│   │
│   ├── system_prompts/          # AI 系统级提示词，用于设定 AI 行为和框架。
│   │   └── CLAUDE.md/           # 包含多版本 AI 系统提示词。
│   │   └── ... (其他系统提示词)
│   │
│   └── user_prompts/            # 用户自定义或常用提示词。
│       └── ... (具体用户提示词文件)
│
├── backups/                     # 项目备份脚本。
│   ├── 一键备份.sh                # 一键执行备份的 Shell 脚本。
│   └── 快速备份.py                # 实际执行逻辑的 Python 脚本，支持 .gitignore 规则。
│
└── libs/                        # 通用库代码，用于项目内部模块化。
    ├── common/                  # 通用功能模块。
    │   └── __init__.py          # Python 包初始化文件。
    └── ... (其他 libs 模块)
