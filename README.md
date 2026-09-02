# Typefully Plugin

The official [Typefully](https://typefully.com) plugin for AI tools. It connects your assistant to your Typefully workspace so you can write, schedule, and publish social media posts on X (Twitter), LinkedIn, Threads, Bluesky, Mastodon, and Substack without leaving your editor.

## What you can do

- Draft posts and threads, cross-posted to every platform you've connected
- Schedule content to your queue at your best times, or publish immediately
- Plan content ahead with dated drafts that never auto-publish until you confirm
- Review upcoming content: browse drafts, your queue, and your posting schedule
- Analyze performance with post metrics and follower growth analytics
- Collaborate through comment threads on drafts
- Attach media with alt text, and tag drafts to stay organized

## How it works

The plugin configures the hosted **Typefully MCP server** in your client:

```
https://mcp.typefully.com/mcp
```

No code runs locally and no credentials are stored in this repository. When your client connects, Typefully opens in your browser and you sign in with OAuth. There is no API key to create or paste. The server advertises standard OAuth discovery (RFC 9728), so any spec-compliant MCP client completes the flow on its own.

The server exposes 26 tools, each with behavior annotations: read-only tools (listing drafts, analytics) are marked as such, and tools with irreversible effects (publishing to a social platform, deleting content) are marked destructive so your client can ask before running them.

## Network endpoints and credentials

For transparency, everything this plugin talks to:

| Endpoint | Purpose |
| --- | --- |
| `https://mcp.typefully.com/mcp` | The MCP server (the only endpoint your client connects to) |
| `https://api.typefully.com` | Typefully's API and OAuth authorization server, called by the MCP server on your behalf |

- Authentication: OAuth 2.0 sign-in in your browser. Headless setups can instead send a Typefully API key as an `Authorization: Bearer` header.
- Access follows your Typefully permissions: on team workspaces, your read/write/publish access level applies to every action.
- This plugin ships no hooks, no scripts, and executes no local code.

## Requirements

A Typefully account (free or paid) with at least one social account connected. Create one at [typefully.com](https://typefully.com).

## Documentation and support

- [Typefully MCP server documentation](https://support.typefully.com/en/articles/13128440-typefully-mcp-server)
- [AI agents overview](https://typefully.com/ai-agents)
- Support: [support.typefully.com](https://support.typefully.com) or support@typefully.com

## License

[MIT](LICENSE)
