# eaispire email assets

Brand image assets for eaispire email templates, served to email clients over
HTTPS from `raw.githubusercontent.com`.

## Why this exists

Email clients cannot load local files, so the HTML template
(`eaispire-email-template.html`, in the agent framework repo) needs absolute
public URLs for its logo and badge images. These files are served from here.

The sender also inlines the same PNGs as base64 data URIs when they are
unreachable, so email still renders in Gmail/Apple Mail if this repo is ever
unavailable. Outlook desktop requires the real URLs.

## Files

| File | Displayed size | Used in |
|---|---|---|
| `eaispire-lockup-white.png` | 152×32 | email header, on navy |
| `eaispire-lockup-navy.png` | 104×22 | email footer, on cream |
| `eaispire-agent01-badge.png` | 58×58 | sign-off avatar |

Source renders are 2× the displayed size for retina. All three are RGBA PNGs,
quantised to keep the base64-inlined payload small enough to stay under Gmail's
100KB clip.

## Base URL

```
https://raw.githubusercontent.com/BotBattleTech/eaispire-email-assets/main
```

That is the `asset_base_url` in `email-config.json` on the agent side. No
trailing slash.

## Rules

- The brand name is lowercase **eaispire** in all copy. Do not retype the
  lockups; replace the PNG files.
- Optimise any replacement with the agent-side `optimize_assets.py` before
  committing, and verify the render visually — not just that the file uploaded.
- Keep file names stable. The template hardcodes them.

## Related

- Sender: `~/eaispire/agents/tools/email/send_eaispire_email.py`
- Hermes skill: `send-eaispire-email`
- Provider API: https://docs.agentmail.to