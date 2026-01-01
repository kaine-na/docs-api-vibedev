# VibeDev API

OpenAI & Anthropic compatible REST API proxy.

**Base URL:** `https://api.vibe-dev.web.id`

---

## Quick Start

```bash
curl https://api.vibe-dev.web.id/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "model": "claude-sonnet-4-5",
    "messages": [{"role": "user", "content": "Hello!"}]
  }'
```

---

## Authentication

Add your API key to the `Authorization` header:

```
Authorization: Bearer YOUR_API_KEY
```

---

## Endpoints

### GET /v1/models

List all available models.

### POST /v1/chat/completions

OpenAI-compatible chat completions.

```json
{
  "model": "claude-sonnet-4-5",
  "messages": [
    {"role": "user", "content": "Hello!"}
  ],
  "max_tokens": 1024,
  "stream": false
}
```

### POST /v1/messages

Anthropic-compatible messages API.

```json
{
  "model": "claude-sonnet-4-5",
  "max_tokens": 1024,
  "messages": [
    {"role": "user", "content": "Hello!"}
  ]
}
```

---

## Models

| Model | Type |
|-------|------|
| `claude-opus-4-5-thinking` | Claude Opus 4.5 + Thinking |
| `claude-sonnet-4-5` | Claude Sonnet 4.5 |
| `claude-sonnet-4-5-thinking` | Claude Sonnet 4.5 + Thinking |
| `gemini-2.5-flash` | Gemini 2.5 Flash |
| `gemini-2.5-flash-lite` | Gemini 2.5 Flash Lite |
| `gemini-3-flash-preview` | Gemini 3 Flash |
| `gemini-3-pro-preview` | Gemini 3 Pro |

---

## SDK Examples

### Python (OpenAI)

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY",
    base_url="https://api.vibe-dev.web.id/v1"
)

response = client.chat.completions.create(
    model="claude-sonnet-4-5",
    messages=[{"role": "user", "content": "Hello!"}]
)
print(response.choices[0].message.content)
```

### Python (Anthropic)

```python
import anthropic

client = anthropic.Anthropic(
    api_key="YOUR_API_KEY",
    base_url="https://api.vibe-dev.web.id"
)

message = client.messages.create(
    model="claude-sonnet-4-5",
    max_tokens=1024,
    messages=[{"role": "user", "content": "Hello!"}]
)
print(message.content[0].text)
```

### JavaScript

```javascript
import OpenAI from 'openai';

const client = new OpenAI({
  apiKey: 'YOUR_API_KEY',
  baseURL: 'https://api.vibe-dev.web.id/v1'
});

const response = await client.chat.completions.create({
  model: 'claude-sonnet-4-5',
  messages: [{ role: 'user', content: 'Hello!' }]
});
console.log(response.choices[0].message.content);
```

---

## Errors

| Code | Description |
|------|-------------|
| 400 | Bad Request |
| 401 | Unauthorized |
| 429 | Rate Limited |
| 500 | Server Error |

---

## Get API Key

Join our Discord server to claim your API key using `/claim` command.
