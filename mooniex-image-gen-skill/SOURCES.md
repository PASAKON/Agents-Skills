# SOURCES — mooniex-image-gen-skill

Unlike the other `mooniex-*-skill` folders in this repo, this is **not** a
merged derivative of third-party skill content. It is a thin operating-manual
wrapper around one external MCP server's tools. No source code or prompt
gallery content is copied here — only tool names and usage guardrails.

| Field | Value |
|---|---|
| Wrapped MCP | `jau123/MeiGen-AI-Design-MCP` |
| Repo | https://github.com/jau123/MeiGen-AI-Design-MCP |
| What's wrapped | 8 MCP tool names (`search_gallery`, `enhance_prompt`, `get_inspiration`, `list_models`, `comfyui_workflow`, `manage_preferences`, `generate_image`, `generate_video`) — names and free/paid split only, per the MCP's own published tool list |
| License review | **Not done.** Publisher is unverified/third-party — supply-chain review is an open item in `mooniex-agents#24`, must clear before the plugin is installed |
| Origin issue | `mooniex-agents#24` (opened 2026-06-21, CEO) |
