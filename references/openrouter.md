# OpenRouter

Unlazy itself is a provider-agnostic completion/verification skill. It does not own the host agent's model transport, so adding network calls to the checker or Stop hook would weaken the existing security and zero-runtime-dependency contract.

Use OpenRouter at the host/agent layer and keep Unlazy unchanged as the verification layer.

## Shared environment convention

For projects that call OpenRouter directly:

```bash
OPENROUTER_API_KEY=...
OPENROUTER_BASE_URL=https://openrouter.ai/api/v1
OPENROUTER_MODEL=~openai/gpt-latest
OPENROUTER_SITE_URL=
OPENROUTER_APP_TITLE=unlazy
```

Never place the real key in a gate ledger, PLAN file, prompt fixture, repository settings file, or committed `.env`.

When a host invokes Unlazy while already using OpenRouter, all gate behavior remains the same: model transport is outside the gate checker, and executable checks continue to use only explicitly approved commands.
