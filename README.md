# claude-skills

A Claude Code plugin that provides easy access to a curated collection of skills I use and recommend. The goal is to make it simple to share useful skills with others — just install the plugin and you're good to go.

## Skills Included

| Skill | Description |
|-------|-------------|
| `show-active-skills` | Lists which skills are active in each response, grouped by scope (user vs project). Gives full transparency into what Claude is doing behind the scenes. |

More skills will be added over time.

## Installation

### From the Claude Code marketplace (recommended)

If the plugin has been published to the official marketplace:

```
/plugins install claude-skills@claude-plugins-official
```

Or browse for it in:

```
/plugins > Discover
```

### From a GitHub repository

You can install directly from the GitHub repo:

```bash
claude plugins add-from-url https://github.com/vsrdouglas/claude-skills.git
```

### From a local clone

```bash
git clone https://github.com/vsrdouglas/claude-skills.git
claude --plugin-dir /path/to/claude-skills
```

## Usage

After installation, the plugin's skills are automatically available in your Claude Code sessions. No extra configuration needed.

To verify the plugin is loaded:

```
/reload-plugins
```

## Contributing

Want to suggest a skill? Open an issue or submit a PR with your skill added to the `skills/` directory following the existing structure:

```
skills/
  your-skill-name/
    SKILL.md
```

## License

MIT
