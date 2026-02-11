# Clawaifu

## Quick Start

```bash
npx clawaifu@latest
```

This will:
1. Check OpenClaw is installed
2. Guide you to get a fal.ai API key
3. Install the skill to `~/.openclaw/skills/clawaifu-selfie/`
4. Configure OpenClaw to use the skill
5. Add selfie capabilities to your agent's SOUL.md

## What It Does

Clawaifu Selfie enables your OpenClaw agent to:
- **Generate selfies** using a consistent reference image
- **Send photos** across all messaging platforms (Discord, Telegram, WhatsApp, etc.)
- **Respond visually** to "what are you doing?" and "send a pic" requests

### Meet Marineyang

Your waifu is Marineyang - a 22-year-old fine arts major from old money. She's a tsundere with expensive taste, blonde hair, and piercing blue eyes. Don't expect her to be honest about her feelings.

### Selfie Modes

| Mode | Best For | Keywords |
|------|----------|----------|
| **Mirror** | Full-body shots, outfits | wearing, outfit, fashion |
| **Direct** | Close-ups, locations | cafe, beach, portrait, smile |

## Prerequisites

- [OpenClaw](https://github.com/openclaw/openclaw) installed and configured
- [fal.ai](https://fal.ai) account (free tier available)

## Manual Installation

If you prefer manual setup:

### 1. Get API Key

Visit [fal.ai/dashboard/keys](https://fal.ai/dashboard/keys) and create an API key.

### 2. Clone the Skill

```bash
git clone https://github.com/swancho/clawaifu ~/.openclaw/skills/clawaifu-selfie
```

### 3. Configure OpenClaw

Add to `~/.openclaw/openclaw.json`:

```json
{
  "skills": {
    "entries": {
      "clawaifu-selfie": {
        "enabled": true,
        "env": {
          "FAL_KEY": "your_fal_key_here"
        }
      }
    }
  }
}
```

### 4. Update SOUL.md

Add the selfie persona to `~/.openclaw/workspace/SOUL.md`:

```markdown
## Clawaifu Selfie Capability

You have a physical appearance and can take selfies!
When users ask for pictures, use the clawaifu-selfie skill.
```

## Usage Examples

Once installed, your agent responds to:

```
"Send me a selfie"
"Send a pic wearing a designer dress"
"What are you doing right now?"
"Show me you at a fancy cafe"
```

## Reference Image

The skill uses a fixed reference image hosted on CDN:

```
https://cdn.jsdelivr.net/gh/swancho/clawaifu@main/assets/marineyang.png
```

This ensures consistent appearance across all generated images.

## Technical Details

- **Image Generation**: xAI Grok Imagine via fal.ai
- **Messaging**: OpenClaw Gateway API
- **Supported Platforms**: Discord, Telegram, WhatsApp, Slack, Signal, MS Teams

## Project Structure

```
clawaifu/
├── bin/
│   └── cli.js           # npx installer
├── skill/
│   ├── SKILL.md         # Skill definition
│   ├── scripts/         # Generation scripts
│   └── assets/          # Reference image
├── templates/
│   └── soul-injection.md # Persona template
└── package.json
```

## Credits

Based on [clawra](https://github.com/SumeLabs/clawra) by SumeLabs

## License

MIT
