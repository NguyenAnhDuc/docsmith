# Docsmith - PRC-010 Documentation Process

Create structured, high-quality documentation following FPT Smart Cloud PRC-010 standard.

## What is Docsmith?

An AI-guided 11-step documentation workflow based on industry best practices from:
- *Docs for Developers* (Bhatti et al., 2021)
- *Strategic Writing for UX* (Podmajersky, 2019)

## Why PRC-010?

- **Systematic:** Repeatable process từ audience analysis đến publication
- **Quality-focused:** Built-in review gates (human + AI)
- **UX-driven:** Voice chart, text patterns, content scorecard
- **Verified:** Automated product walkthrough với screenshots

## Installation

### Claude Code (Recommended)
```bash
# Add marketplace
/plugin marketplace add fpt-smartcloud/docsmith

# Install
/plugin install fpt-smartcloud/docsmith
```

### Manual Install
```bash
# Personal scope (all projects)
git clone https://github.com/fpt-smartcloud/docsmith.git ~/.claude/skills/docsmith

# Project scope (current project only)
git clone https://github.com/fpt-smartcloud/docsmith.git .claude/skills/docsmith
```

## Quick Start

```bash
# Start full workflow
/docsmith start MyProduct

# Or run individual steps
/docsmith audience MyProduct     # Define audience & goals
/docsmith plan MyProduct         # AI generates doc plan
/docsmith review-plan MyProduct  # Human review
/docsmith sitemap MyProduct      # AI creates structure
/docsmith voice MyProduct        # AI defines UX standards
/docsmith draft MyProduct        # AI writes docs
/docsmith edit MyProduct         # AI self-review (5 passes)
/docsmith walkthrough MyProduct  # AI tests on real product
/docsmith verify MyProduct       # Run all checks
/docsmith publish MyProduct      # Final approval
```

## Workflow Steps

```
1. audience (Human)      → Define target users, goals, personas
2. plan (AI)             → Documentation plan + traceability matrix
3. review-plan (Human)   → Approve plan
4. sitemap (AI)          → Folder structure, navigation, cross-links
5. voice (AI)            → Voice chart, UX patterns, scorecard
6. draft (AI)            → Write documentation
7. edit (AI)             → Self-review (5 passes)
8. walkthrough (AI)      → Test on product + screenshots
9. peer-review (Human)   → Review docs
10. tech-review (Human)  → Optional technical review
11. incorporate (AI)     → Integrate feedback
12. publish (Human)      → Final approval & release
```

## Commands Reference

| Command | Description |
|---------|-------------|
| `help` | Show command reference |
| `start` | Begin full process |
| `audience` | Define audience & goals |
| `plan` | AI creates documentation plan |
| `review-plan` | Human review gate |
| `sitemap` | AI creates structure |
| `voice` | AI defines UX content standards |
| `draft` | AI writes documentation |
| `edit` | AI self-review (5 passes) |
| `walkthrough` | AI tests on real product |
| `validate` | Re-run walkthrough tests |
| `test` | Create test cases from docs |
| `verify` | Run all verification checks |
| `peer-review` | Human peer review |
| `tech-review` | Human technical review |
| `incorporate` | AI integrates feedback |
| `publish` | Human final approval |

## Examples

**Document new API endpoint:**
```bash
/docsmith start PaymentAPI
# Follow prompts for audience → plan → draft → walkthrough → publish
```

**Update existing docs:**
```bash
/docsmith draft UserManagement     # Update docs only
/docsmith verify UserManagement    # Check quality
```

**Run verification only:**
```bash
/docsmith validate MyProduct                         # Test all
/docsmith verify MyProduct docs/drafts/api-*.md     # Scope to API docs
```

## Output Structure

All outputs saved to `docs/` folder:
```
docs/
├── plan/                 # Documentation plans, traceability matrix
├── standards/            # Voice chart, UX patterns, scorecard
├── drafts/              # Draft documents
├── walkthrough/         # Test results, validation
└── images/              # Screenshots from walkthrough
```

## Templates Included

- Audience Profile
- Documentation Plan
- Traceability Matrix
- Voice Chart
- UX Text Patterns
- UX Content Scorecard
- Content Type Templates (Getting Started, Tutorials, Reference, etc.)
- Walkthrough Test Cases

## Cross-Platform Compatibility

Works with:
- ✅ Claude Code (native support via `/docsmith`)
- ✅ Cursor (Agent Skills)
- ✅ GitHub Copilot (Agent Skills)
- ✅ OpenAI Codex CLI

*Note: Slash commands are Claude Code-specific. Other tools use SKILL.md as context.*

## License

MIT

## Author

FPT Smart Cloud

## Support

- GitHub Issues: https://github.com/fpt-smartcloud/docsmith/issues
- Docs: See [SKILL.md](SKILL.md) for detailed process reference

## Changelog

See [CHANGELOG.md](CHANGELOG.md)
