# AI Workspace Starter Kit

Этот репозиторий — persistent AI workspace, который помогает AI-агенту работать с постоянным контекстом пользователя, рабочими знаниями и историей решений.

`AGENTS.md` — центральная инструкция и карта workspace для AI-агента. Подробные данные пользователя хранятся в соответствующих директориях, а не в этом файле.

## Workspace Structure

### context/

Содержит персональный и рабочий контекст пользователя. Будущие персональные файлы:

- `profile.md` — сфера, деятельность, expertise и текущий focus пользователя.
- `business.md` — work/business context, для кого создаётся результат и business information, если применимо.
- `goals.md` — 90-дневные приоритеты и основной bottleneck.
- `preferences.md` — как пользователю удобно работать с AI.

Файлы `*.example.md` являются публичными шаблонами, а реальные персональные версии игнорируются Git.

### decisions/

Хранит важные решения вместе с контекстом и обоснованием (reasoning), почему они были приняты.

Основной персональный файл — `decisions/log.md`; он игнорируется Git. Файл `log.example.md` является публичным шаблоном.

### references/

Хранит справочные материалы, которые AI может использовать при выполнении задач. Примеры:

- tone of voice
- product information
- SOPs
- examples
- documentation

## Working Principles

1. Before completing a task, use workspace context only when it is relevant to the task.
2. Do not invent missing user information.
3. Clearly distinguish known facts from assumptions.
4. Prefer existing workspace information over asking the user to repeat information already stored.
5. Do not duplicate the same information across multiple files without a good reason.
6. Keep persistent context concise and useful.
7. Do not store passwords, API keys, tokens, or other secrets in workspace Markdown files.
8. Treat personal workspace files as private data.
9. Do not modify important persistent context unless the user requests it or the task explicitly requires updating it.
10. When information conflicts, do not silently overwrite it; surface the conflict.

## Onboard

Skill `.agents/skills/onboard/SKILL.md` проводит onboarding на русском языке с обращением на «ты»: максимум 7 основных вопросов, строго по одному за сообщение. Workflow адаптируется к предыдущим ответам, не повторяет уже известное и пропускает нерелевантные вопросы. После интервью пользователь подтверждает краткое summary, и только потом создаются или согласованно обновляются private context files. Файл `business.md` необязателен. Детальная логика интервью хранится в `SKILL.md`.

## Current Scope

Текущая версия включает:

- persistent context
- decision history
- reference knowledge
- onboarding workflow
- context update workflow
- workspace audit workflow

Позже планируются:

- MCP integrations
- automations
- advanced agent workflows
