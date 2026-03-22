# Changelog

All notable changes to the WISC JS Framework will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Planned
- Matt Pocock enhancements (grill-me, ubiquitous-language)
- Real project examples from completed builds
- Domain-specific skills (mortgage, agency, sports)
- Video tutorials and walkthroughs

---

## [1.0.0] - 2025-03-22

### Added - Initial Release

#### Core Framework
- `.claude/rules.md` - Global rules adapted for JavaScript/Supabase stack
- `.claude/commands/prime.md` - Codebase exploration before planning
- `.claude/commands/plan.md` - Structured implementation planning
- `.claude/commands/execute.md` - Implementation from plan in fresh session
- `.claude/commands/commit.md` - Standardized git commits with AI layer tracking
- `.claude/commands/handoff.md` - Session transfer when context exceeds 150K tokens

#### Context Files (On-Demand Loading)
- `.claude/context/agents.md` - Multi-agent orchestration patterns via Supabase
- `.claude/context/database.md` - Supabase/PostgreSQL patterns (RLS, migrations, Edge Functions)
- `.claude/context/frontend.md` - React/Next.js patterns (App Router, hooks, forms)

#### Documentation
- `SETUP-GUIDE.md` - Installation and first-time setup instructions
- `QUICK-REFERENCE.md` - Daily workflow cheat sheet
- `COMPLETE-WALKTHROUGH.md` - Full digital agency platform example

#### Directory Structure
- `plans/` - Storage for implementation plans (created by /plan command)
- `handoffs/` - Storage for session transfer documents (created by /handoff command)
- `.claude/skills/` - Placeholder for reusable capability modules
- `.claude/docs/` - Placeholder for deep-dive documentation

#### Key Features
- NO n8n rule (pure JavaScript automation)
- Supabase-first architecture (database, auth, storage, realtime)
- Multi-agent coordination via Supabase task queues
- VPS deployment patterns (Hostinger + PM2 + Claude Code CLI)
- Template-first philosophy (frameworks over implementations)

#### Workflow Commands
- `/prime` - Explore codebase (git log, structure, dependencies)
- `/plan` - Create detailed implementation plan (3-5K tokens)
- `/execute [plan-path]` - Implement from plan in fresh session
- `/commit` - Standardized commits (code changes + AI layer improvements)
- `/handoff` - Create session transfer document (when >150K tokens)

#### Token Budget Guidelines
- Planning Session: < 50K tokens target, 80K max
- Implementation Session: < 100K tokens target, 150K max
- Handoff Document: 3-5K tokens target, 5K max
- Commit Message: < 1K tokens

### Design Decisions

#### Why Separate Planning from Implementation
Prevents context rot by keeping sessions focused. Plans contain ALL context needed for fresh implementation sessions.

#### Why Git Log as Memory
Standardized commits create searchable long-term memory. Future sessions use git log to catch up on recent work.

#### Why Sub-Agents for Research
Isolates heavy research (10K-100K tokens) from main context. Sub-agents return compressed summaries (< 5K tokens).

#### Why Just-In-Time Context Loading
Loads only relevant context files when working on specific areas. Prevents bloat from loading everything "just in case."

#### Why Fresh Sessions Over Compression
When context exceeds 150K tokens, handoff to fresh session rather than compressing. Maintains performance and reduces hallucinations.

---

## How to Use This Changelog

### For Users
- Check [Unreleased] to see what's coming
- Check version numbers to see what changed when
- Use version tags when reporting issues

### For Maintainers
When making changes:

1. **Add to [Unreleased]** section while working
2. **Move to new version** when releasing
3. **Follow categories**:
   - `Added` - New features
   - `Changed` - Changes to existing features
   - `Deprecated` - Soon-to-be-removed features
   - `Removed` - Removed features
   - `Fixed` - Bug fixes
   - `Security` - Security fixes

4. **Use semantic versioning**:
   - MAJOR version - Breaking changes
   - MINOR version - New features (backwards compatible)
   - PATCH version - Bug fixes (backwards compatible)

### Version History Template

```markdown
## [X.Y.Z] - YYYY-MM-DD

### Added
- New feature descriptions

### Changed
- Changes to existing features

### Fixed
- Bug fix descriptions

### Removed
- Removed feature descriptions
```

---

## Version Numbering

**Current Version**: 1.0.0

**Next Expected**:
- 1.1.0 - When Matt Pocock enhancements added
- 1.2.0 - When first real project examples added
- 2.0.0 - If breaking changes to core workflow

---

**Note**: This framework is under active development. Expect frequent updates as it's refined through real-world use.
