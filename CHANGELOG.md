# Changelog

Version is tracked in `SKILL.md` under `metadata.mystilink.version` and in this file.

## 0.1.0

- Agent Skill that routes a request to one Mystilink metaphysics skill (BaZi, Zi Wei, tarot, Liu Yao, western horoscope)
- Routing rules in `SKILL.md` cover unnamed systems, mixed traditions, and clarification cases
- `references/overview.md` summarizes each target system and when to prefer it
- `examples/routing-cases.md` lists sample requests and the expected target skill
- Runtime: no local dependencies; the Wiki lookup is optional
- Install by copying this directory into a host skills path that reads `SKILL.md`
