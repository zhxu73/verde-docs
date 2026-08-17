# Codex

You can follow these instructions to use your VERDE API Key after installing Codex. More information on using Codex can be found here, https://docs.anthropic.com/en/docs/intro.

## Prerequisites

1. Your VERDE course or team must be configured to use Anthropic models (see instructor or team lead)
2. Obtain your VERDE API Key. [Instructions can be found here](api-token.md)
3. Install Codex. Instructions can be found here, https://github.com/openai/codex
4. The remaining instructions assume you have an open terminal on system with Codex and bash installed.

## 1. Setup the Codex configuration file

Codex save its configuration at `~/.codex/config.toml`, add the following content to the configuration file (do not overwrite the existing content), replacing`<your-model-name>` with the model you'd like to use.

```toml
model = "<your-model-name>"
model_provider = "verde"
model_reasoning_effort = "medium" # change this if you want to adjust the reasoning effort for the model
approvals_reviewer = "user" # change this if you want to adjust the reviewer for approvals, other options is "auto_review"

[model_providers.verde]
name = "verde"
base_url = "https://llm-api.cyverse.ai/v1"
env_key = "VERDE_API_KEY"
wire_api = "responses"
stream_idle_timeout_ms = 7200000
stream_max_retries = 5
request_max_retries = 4
```

Export the following environment variables before launching Codex (replacing `<your-ai-verde-api-key>` with your VERDE API Key).

```bash
export VERDE_API_KEY="<your-ai-verde-api-key>"
```

To avoid re-entering this each session, add the line to your shell profile (e.g. `~/.bashrc` or `~/.zshrc`). Then, you can source your shell profile.

## 2. Start Codex

You can then run Codex.
```
codex
```

## If you need to change your `VERDE_API_KEY`

If for some reason you need to change your VERDE API Key, simply re-set the `VERDE_API_KEY` environment variable, then restart Codex.
