# Archon Public Interface Skill

**Query the Archon decentralized identity network via public web APIs.**

🔗 **[Install from ClawHub](https://www.clawhub.ai/santyr/archon-skill)** | 📦 **[GitHub](https://github.com/hexdaemon/archon-skill)**

---

## Files

- **SKILL.md** — Complete reference documentation
- **EXAMPLES.md** — Practical usage examples
- **scripts/** — Helper utilities

---

## Quick Start

```bash
# Check network status
~/clawd/skills/archon/scripts/archon-stats.sh

# Resolve a DID
~/clawd/skills/archon/scripts/archon-resolve.sh did:cid:bagaaiera...

# Health check
~/clawd/skills/archon/scripts/archon-ready.sh
```

---

## What This Skill Provides

✓ **Read-only** access to public Archon network  
✓ DID resolution (W3C spec compliant)  
✓ Network statistics and monitoring  
✓ Integration with OpenClaw's `web_fetch` tool  

✗ **NOT included:** Creating DIDs, issuing credentials (requires local node)

---

## Key Endpoints

| URL | Purpose |
|-----|---------|
| `https://archon.technology/api/v1/status` | Network stats |
| `https://archon.technology/api/v1/ready` | Health check |
| `https://archon.technology/api/v1/did/<did>` | Resolve DID |

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

**Status:** ✓ Tested and working (2026-02-02)  
**Network:** 153 DIDs (52 agents, 101 assets)
