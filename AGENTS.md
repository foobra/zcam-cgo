<!-- OPENSPEC:START -->
# OpenSpec Instructions

These instructions are for AI assistants working in this project.

Always open `@/openspec/AGENTS.md` when the request:
- Mentions planning or proposals (words like proposal, spec, change, plan)
- Introduces new capabilities, breaking changes, architecture shifts, or big performance/security work
- Sounds ambiguous and you need the authoritative spec before coding

Use `@/openspec/AGENTS.md` to learn:
- How to create and apply change proposals
- Spec format and conventions
- Project structure and guidelines

Keep this managed block so 'openspec update' can refresh the instructions.

<!-- OPENSPEC:END -->
始终使用中文回复
尽量使用中文来写openspec的文档
原始需求都在_specs目录下的md文档中. md文档中的 # prd 章节代表业务需求, # tech代表技术需求

openspec 的提案, 名称前面都需要添加日期, 例如 241031等. 形成 240505-xxxx 这种

实现代码的时候, 一定要最小化,最简化,不要引多余的代码和依赖,一切从简,只完成spec要求的能力