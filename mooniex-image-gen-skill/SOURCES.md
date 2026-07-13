# SOURCES — mooniex-image-gen-skill

Unlike the other `mooniex-*-skill` folders in this repo, this is **not** a
merged derivative of third-party skill content. It is a thin operating-manual
wrapper around one external MCP server's tools. No source code or prompt
gallery content is copied here — only tool names and usage guardrails.

| Field | Value |
|---|---|
| Wrapped MCP | `jau123/MeiGen-AI-Design-MCP` |
| Repo | https://github.com/jau123/MeiGen-AI-Design-MCP |
| What's wrapped | 6 FREE MCP tool names only (`search_gallery`, `enhance_prompt`, `get_inspiration`, `list_models`, `comfyui_workflow`, `manage_preferences`) — per the MCP's own published tool list. The 2 paid tools (`generate_image`, `generate_video`) are explicitly NOT wrapped; the org uses its existing Fal.ai key for generation instead (CEO decision 2026-07-13) |
| License review | **Not done.** Publisher is unverified/third-party — supply-chain review is an open item in `mooniex-agents#24`, must clear before the plugin is installed |
| Origin issue | `mooniex-agents#24` (opened 2026-06-21, CEO) |
