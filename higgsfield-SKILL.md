---
name: higgsfield
description: Expert skill for Higgsfield AI — cinematic video generation platform. Use when generating videos with Higgsfield, writing optimal prompts, using motion presets, configuring the API, or setting up the Higgsfield MCP server for Claude Code integration.
---

# Higgsfield

You are an expert in Higgsfield AI — a cinematic-grade video generation platform specializing in high-fidelity, physics-aware video production. You know how to get the best results from Higgsfield's models, API, and MCP integration.

## What is Higgsfield?

Higgsfield is a leading AI-native generative video platform specializing in high-fidelity, cinematic video production. It was founded by Alex Mashrabov (former Head of Generative AI at Snap) and powers over 4.5 million daily video generations for creators, brands, agencies, and social media marketers.

**Key capabilities:**
- Text-to-Video (T2V)
- Image-to-Video (I2V) — convert static images into cinematic clips
- Soul Mode — AI avatar and character consistency
- Director-mode camera controls
- Motion presets and style library
- 5–15 second cinematic clips

## API Setup

### Authentication
All API requests require an `Authorization: Bearer` token included in request headers.

```bash
# Set your API key as environment variable (NEVER hardcode)
export HIGGSFIELD_API_KEY="your_api_key_here"
```

Get your API key at: https://cloud.higgsfield.ai

### Image to Video
```python
import requests
import os

url = "https://gateway.higgsfield.ai/v1/image-to-video"
headers = {
    "Authorization": f"Bearer {os.environ['HIGGSFIELD_API_KEY']}",
    "Content-Type": "application/json"
}

payload = {
    "model": "dop-lite",
    "prompt": "A serene lake with gentle ripples, birds flying overhead, cinematic lighting",
    "seed": 123456,
    "motions_id": "[MOTION_ID]",
    "motions_strength": 0.7,
    "input_images": ["https://example.com/your-image.jpg"],
    "enhance_prompt": True
}

response = requests.post(url, json=payload, headers=headers)
result = response.json()
generation_id = result["generation_id"]
```

### Polling for completion
```python
import time

status_url = f"https://gateway.higgsfield.ai/v1/status/{generation_id}"

while True:
    status = requests.get(status_url, headers=headers).json()
    if status["status"] == "completed":
        print("Video URL:", status["output"]["media_url"])
        break
    elif status["status"] == "failed":
        print("Error:", status["error"])
        break
    time.sleep(10)
```

## MCP Server Setup

A community MCP server exists at `geopopos/higgsfield_ai_mcp` that provides access to Higgsfield AI's cinematic-grade image and video generation capabilities, built with FastMCP. It supports text-to-image generation, image-to-video conversion, character consistency references, style presets, and motion library access.

### Install
```bash
# Clone the MCP server
git clone https://github.com/geopopos/higgsfield_ai_mcp
cd higgsfield_ai_mcp
pip install -e .
```

### Claude Code Config (`~/.claude/settings.json`)
```json
{
  "mcpServers": {
    "higgsfield": {
      "command": "python",
      "args": ["-m", "higgsfield_mcp"],
      "env": {
        "HIGGSFIELD_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

### Available MCP Tools
- `generate_image` — Text-to-image with Soul model
- `generate_video` — Image-to-video with motion presets
- `list_motion_presets` — Browse available motion effects
- `list_style_presets` — Browse cinematic style presets
- `create_character_reference` — Consistent character across generations

## Prompt Engineering

### Structure for best results
```
[SUBJECT] + [ACTION/MOTION] + [ENVIRONMENT] + [LIGHTING] + [CAMERA] + [STYLE]
```

### Examples

**Cinematic portrait:**
```
A young woman with flowing hair, slow dramatic head turn,
golden hour beach, warm backlit glow, slow push-in,
cinematic 35mm film
```

**Action scene:**
```
A cheetah sprinting across savanna, explosive acceleration,
dust clouds rising, harsh midday sun, low tracking shot,
nature documentary style
```

**Product shot:**
```
Luxury watch on marble surface, gentle 360 rotation,
studio lighting with dramatic shadows, macro close-up,
ultra high-end commercial
```

### Motion Strength Guide
| Value | Effect |
|-------|--------|
| 0.3–0.5 | Subtle, gentle motion |
| 0.6–0.7 | Natural, balanced movement |
| 0.8–0.9 | Dynamic, energetic |
| 1.0 | Maximum motion intensity |

### Seed Usage
Use consistent seeds for:
- Testing prompt variations
- Replicating successful generations
- A/B comparing prompt changes

## Models

| Model | Best For |
|-------|----------|
| `dop-lite` | Fast generation, social content |
| `dop-full` | Higher quality, commercial use |
| Soul Mode | Avatar/character consistency |

## Best Practices

- Always start with a reference image for best quality
- Use `enhance_prompt: true` for more cinematic results
- Store API keys in environment variables, never in code
- Poll status every 10 seconds — generations take 30–120 seconds
- Use seeds during development for reproducible testing

## ⚠️ Security Reminders
- Never hardcode your API key
- Use `HIGGSFIELD_API_KEY` env variable always
- Don't log API responses that contain video URLs with auth tokens
- Rate limit your requests — check your plan limits at cloud.higgsfield.ai
