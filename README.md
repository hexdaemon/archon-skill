# ⚠️ DEPRECATED — Use the official Archon agent skills repo

> **This repo is no longer maintained.** The official, up-to-date Archon skill is at:
>
> 👉 **https://github.com/archetech/agent-skills/tree/main/archon-keymaster**
>
> The `archon-keymaster` skill includes everything from this repo plus new features: digital asset management, improved identity scripts, vault member management, and more.

---

# Archon Identity Skill (Legacy)

**Full Archon decentralized identity operations - local node management, DID creation, credential issuance, vault operations, and public network access.**

🔗 **[Official Skill](https://github.com/archetech/agent-skills/tree/main/archon-keymaster)** | 📦 **[Legacy GitHub](https://github.com/hexdaemon/archon-skill)**

---

## Platform Support

✅ **All platforms (recommended):** Keymaster CLI via npm (`npx @didcid/keymaster`)  
✅ **Linux/macOS:** Full support (local node optional)  
⚠️ **Windows:** WSL2 recommended for local node (see WINDOWS.md)

**Cross-platform operations (no node required):**
- Public API queries
- Keymaster CLI via npx (Node.js only)
- DID creation and management via CLI

---

## Files

- **SKILL.md** — Complete reference documentation
- **EXAMPLES.md** — Practical usage examples
- **WINDOWS.md** — Windows-specific setup guide
- **scripts/** — Helper utilities (cross-platform)

---

## Quick Start

**Public network operations (all platforms):**
```bash
# Check network status
~/clawd/skills/archon/scripts/archon-stats.sh

# Resolve a DID
~/clawd/skills/archon/scripts/archon-resolve.sh did:cid:bagaaiera...
```

**Local node operations (requires local Archon node):**
```bash
# List your DIDs
~/clawd/skills/archon/scripts/archon-list-ids.sh

# List credentials
~/clawd/skills/archon/scripts/archon-list-credentials.sh

# Create new DID
~/clawd/skills/archon/scripts/archon-create-did.sh "name" "agent"

# Backup to vault
~/clawd/skills/archon/scripts/archon-vault-backup.sh vault-name file.db backup-key
```

---

## What This Skill Provides

**Public Network (Read-Only, All Platforms):**
✓ DID resolution (W3C spec compliant)  
✓ Network statistics and monitoring  
✓ Health checks  
✓ Integration with OpenClaw's `web_fetch` tool  

**Local Node (Full Capabilities, Requires Docker):**
✓ Create and manage DIDs  
✓ Issue verifiable credentials  
✓ Encrypted vault storage  
✓ Group management  
✓ Document signing  
✓ Cross-platform identity linking

---

## Recommended Path (Pre‑Alpha)

**Use the npm package (Keymaster CLI) — no local Archon node required.**
This is the safest path while the Archon node stack is still pre‑alpha.

```bash
# Use directly
npx @didcid/keymaster list-ids
npx @didcid/keymaster create-id --name "agent-name" --type agent
```

Local nodes are **advanced / experimental** and should be used only if you need
vaults, signing, or on‑chain anchoring.

---

## Local Node Setup (Advanced / Experimental)

For full capabilities, run a local Archon node:

🔧 **[Install Archon locally](https://github.com/archetech/archon)** — Docker-based, includes keymaster + gatekeeper

**Installation:**
```bash
# Clone and start
git clone https://github.com/archetech/archon ~/archon
cd ~/archon
docker compose up -d

# Verify running
curl http://localhost:4226/api/v1/ready  # Keymaster
curl http://localhost:4224/api/v1/ready  # Gatekeeper
```

**Configuration:**
```bash
export ARCHON_CONFIG_DIR="$HOME/.config/archon"
export ARCHON_PASSPHRASE="your-secure-passphrase"
mkdir -p "$ARCHON_CONFIG_DIR"
```

**Windows users:** See WINDOWS.md for platform-specific setup.

---

## Key Endpoints

**Public Network:**
| URL | Purpose |
|-----|---------|
| `https://archon.technology/api/v1/status` | Network stats |
| `https://archon.technology/api/v1/ready` | Health check |
| `https://archon.technology/api/v1/did/<did>` | Resolve DID |

**Local Node (if running):**
| URL | Purpose |
|-----|---------|
| `http://localhost:4226` | Keymaster (wallet operations) |
| `http://localhost:4224` | Gatekeeper (DID resolution) |
| `http://localhost:4228` | Web wallet UI |
| `http://localhost:3003` | Grafana metrics |

---

## Use Cases

1. **Verify credentials** — Check if issuer DID exists
2. **Monitor network** — Track growth and health
3. **Identity discovery** — Explore agent DIDs
4. **Cross-platform** — Link Archon + Nostr identities

---

## See Also

- **TOOLS.md** → Archon Server (local node for full R/W access)
- **Nostr skill** → Cross-identity with NIP-05
- **HexMem** → Store resolved DIDs as facts

---

## Verification

All commits are signed with Archon DID:
```
did:cid:bagaaieratn3qejd6mr4y2bk3nliriafoyeftt74tkl7il6bbvakfdupahkla
```

The `manifest.json` file contains SHA256 hashes of all repo files, cryptographically signed. Verify with:

```bash
npx @didcid/keymaster verify-file manifest.json
```

To regenerate after changes (requires ARCHON_PASSPHRASE):
```bash
./scripts/sign-repo.sh
```

---

**Status:** ✓ Tested and working (2026-02-02)  
**Network:** 153 DIDs (52 agents, 101 assets)
