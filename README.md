# 🔐 Token Visualizer — OBO & XAA / ID-JAG

> Decode, inspect, and verify OAuth 2.0 delegation chains — **no install, no server, runs locally as a desktop app.**

![Platform](https://img.shields.io/badge/platform-Windows-blue?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)
![Standards](https://img.shields.io/badge/RFC-8693%20%7C%207523%20%7C%20ID--JAG-orange?style=flat-square)
![Okta](https://img.shields.io/badge/works%20with-Okta%20%7C%20Auth0%20%7C%20xaa.dev-lightgrey?style=flat-square)

---

## What it does

Paste your real tokens. See every claim decoded, highlighted, and verified — without sending anything to a server.

| Mode | What it verifies |
|---|---|
| **OBO (On-Behalf-Of)** | `sub` preservation · client_id actor · downstream scopes — RFC 8693 |
| **XAA / ID-JAG** | ID Token → ID-JAG → Access Token chain · iss/aud alignment · TTL ≤ 10 min · typ claim |

---

## Screenshots

> *(Add your screenshots to `/screenshots` folder and they appear here)*

---

## Features

- **OBO flow** — paste User token + OBO token, get chain proof with `sub` preservation check
- **XAA / ID-JAG flow** — 4-tab inspector: ID Token · ID-JAG · Access Token · Chain Proof
- **6 automated chain checks** — sub match, issuer match, delegation handoff, typ claim, TTL, scope consistency
- **Dark mode** — automatic via `prefers-color-scheme`
- **Zero network calls** — all decoding is `atob()` + `JSON.parse()` in your browser
- **Desktop app experience** — opens in Edge/Chrome `--app` mode (no address bar, no tabs)
- **Single file** — one `.vbs` double-click, no dependencies, no install

---

## How to use

### Quickest start (zero warning, recommended)

1. Download [`TokenVisualizer.zip`](../../releases/latest)
2. Right-click the ZIP → **Properties → tick Unblock → Apply**
3. Extract → double-click `TokenVisualizer.vbs`

### Direct VBS

1. Download `TokenVisualizer.vbs`
2. Double-click → click **Open** on the one-time warning
3. The file self-unblocks — no warning on any future run

---

## Supported token formats

| Token | Source | Claims inspected |
|---|---|---|
| User access token | Okta PKCE login | `sub`, `scp`, `cid`, `uid` |
| OBO token | RFC 8693 token exchange | `sub`, `client_id`, `scope`, `uid` |
| OIDC ID Token | Any OIDC provider | `sub`, `iss`, `aud` |
| ID-JAG | xaa.dev / Okta XAA | `sub`, `iss`, `aud`, `typ`, `scope`, TTL |
| XAA Access Token | Resource auth server | `iss`, `aud`, `sub`, `scope`, `app_org` |

Accepts raw JWT strings (`eyJ...`) and JSON objects `{...}`.

---

## Standards implemented

| Standard | Used for |
|---|---|
| [RFC 8693](https://www.rfc-editor.org/rfc/rfc8693) | OAuth 2.0 Token Exchange (OBO + XAA step 2) |
| [RFC 7523](https://www.rfc-editor.org/rfc/rfc7523) | JWT Bearer Grant (XAA step 3) |
| [RFC 6750](https://www.rfc-editor.org/rfc/rfc6750) | Bearer Token Usage |
| [ID-JAG draft](https://datatracker.ietf.org/doc/draft-ietf-oauth-identity-assertion-authz-grant/) | Identity Assertion Authorization Grant |
| [OIDC Core](https://openid.net/specs/openid-connect-core-1_0.html) | ID Token structure |

---

## Privacy

- All token decoding happens **locally in your browser**
- No tokens are sent to any server — ever
- The VBS writes a static HTML file to `%APPDATA%` and opens it in Edge/Chrome app mode
- Works completely offline after download

---

## Signing (optional — removes Unknown Publisher warning)

If your organisation requires signed scripts, a companion script creates a free self-signed certificate:

```powershell
# Right-click Sign_TokenVisualizer.ps1 → Run with PowerShell
# Uses only built-in Windows tools — no purchase needed
# Shows "Shashi Singh | SRA Holding BV" as publisher
```

See [`Sign_TokenVisualizer.ps1`](Sign_TokenVisualizer.ps1) for details.

---

## Author

**Shashi Singh**  
Senior IAM Solutions Architect · Enterprise Security Architect  
[SRA Holding BV](https://sraholding.nl) · Aalsmeer, Netherlands  
CISSP · TOGAF · SABSA · CISA · AZ-500

---

## License

[MIT](LICENSE) — free to use, modify, and distribute with attribution.

---

## Related tools & standards

- [xaa.dev](https://xaa.dev) — XAA/ID-JAG playground
- [jwt.io](https://jwt.io) — JWT decoder (online, sends tokens to server)
- [Okta Cross-App Access docs](https://developer.okta.com/docs/guides/ai-agent-token-exchange/-/main/)
- [ID-JAG IETF draft](https://datatracker.ietf.org/doc/draft-ietf-oauth-identity-assertion-authz-grant/)

