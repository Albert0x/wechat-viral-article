<!-- 语言切换 Language -->
[简体中文](README.md) | **English**

# Workplace Boundaries · WeChat Viral Article Skill

A custom Skill for [Claude](https://claude.com/claude-code) that helps write articles for the WeChat Official Account "职场边界局" (Workplace Boundaries).

It targets **workplace emotions / personal growth / the plight of ordinary workers in the AI era**, using the proven viral structure: pain-point opening → parallel sub-arguments → supporting cases → punchy takeaways → call to follow & share.

## Contents

```
wechat-viral-article/
├── SKILL.md                        # Core skill (writing skeleton, topics, structure, case bank, anti-AI-detection tips)
└── references/
    ├── wechat-publishing.md        # Generate paste-ready HTML for the WeChat editor
    └── image-guide.md              # Image guidance (cover mood, stock-photo keywords, AI image prompts)
wechat-viral-article.skill          # Packaged, installable file
```

## Install & Use

**Option 1: Install the packaged file**

Download `wechat-viral-article.skill` and import it in Claude Code / the desktop app.

**Option 2: Drop into your skills directory**

Place the `wechat-viral-article/` folder into your Claude skills directory and restart.

Once installed, the skill triggers automatically when you ask to "write an article about X" in a workplace / growth / AI context.

## Features

- **Complete output**: title (with alternatives), cover copy, epigraph, opening hook, body with sub-arguments, closing call-to-action
- **Case bank**: four source types — TV/film characters, celebrity anecdotes, psychology concepts, classic quotes
- **Anti-AI-detection tips**: built-in guidance to make the writing read more "human"
- **Paste-ready layout**: generates inline-styled HTML you can select-all and paste straight into the WeChat editor
- **Image guidance**: each article comes with cover-image mood, stock-photo keywords, and an AI image prompt

## Note

This Skill was created with the help of [Claude Code's skill-creator](https://claude.com/claude-code).
