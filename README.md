# WISC JS Framework

> A context management system for building reliable AI-powered applications with Claude Code. Adapted from Cole Medin's WISC framework for JavaScript/Supabase stack.

## What This Is

**WISC** (Write, Isolate, Select, Compress) is a battle-tested approach to managing context when building with AI coding assistants. This framework prevents context rot, eliminates hallucinations, and creates consistent, repeatable builds.

**This version** is adapted specifically for:
- ✅ JavaScript/Node.js (no Python)
- ✅ Supabase (database, auth, storage, edge functions)
- ✅ Multi-agent architectures via Supabase coordination
- ✅ Pure JavaScript automation (NO n8n, NO low-code)
- ✅ VPS deployment patterns (Hostinger + Claude Code CLI)

## The Problem WISC Solves

When building with AI coding assistants, you hit the same problems:
- **Context rot**: Sessions exceed 150K tokens, agent starts hallucinating
- **Vocabulary drift**: Claude uses different terms across sessions
- **Inconsistent builds**: No systematic approach, every build is chaotic
- **Wasted tokens**: Building → realize requirements were wrong → rebuild
- **Lost progress**: Context resets, Claude forgets what was built

## The Solution

A **systematic build framework** with clear workflows:

### W = Write (Externalize Memory)
- Git log as long-term memory (via `/commit` command)
- Implementation plans (via `/plan` command)
- Session handoffs (via `/handoff` command)

### I = Isolate (Use Sub-Agents)
- Research agents for codebase exploration
- Parallel research without bloating main context
- Sub-agents return summaries, not full transcripts

### S = Select (Just-In-Time Context)
- Global rules always loaded (< 700 lines)
- On-demand context files (frontend, backend, database, agents)
- Skills loaded only when needed
- Prime commands for fresh codebase exploration

### C = Compress (Avoid When Possible)
- Handoffs when context > 150K tokens
- Fresh sessions preferred over compression
- Best compression = not needing compression

## Quick Start

### Installation

```bash
# Clone this repo
git clone https://github.com/yourusername/wisc-js-framework.git

# Copy core framework into your project
cd your-project
cp -r /path/to/wisc-js-framework/core/.claude ./
mkdir plans handoffs

# Done! Start using it
```

### Your First Build

```bash
# Open Claude Code in VSCode
# Run commands in order:

/prime      # Explore codebase (git log, structure, recent changes)
/plan       # Create detailed implementation plan

# Close session, start NEW session
/execute plans/[your-plan].md   # Implement from plan
/commit     # Standardized commit with AI layer tracking
```

## What's Included

### Core Framework (`core/`)
- **`.claude/rules.md`** - Global rules (always loaded)
- **`.claude/commands/`** - Workflow commands (prime, plan, execute, commit, handoff)
- **`.claude/context/`** - On-demand context (agents, database, frontend)
- **`.claude/skills/`** - Reusable capability patterns (you build these)
- **`.claude/docs/`** - Deep-dive documentation (you build these)
- **`plans/`** - Implementation plans storage
- **`handoffs/`** - Session transfer documents

### Documentation (`docs/`)
- **SETUP-GUIDE.md** - Installation and first-time setup
- **QUICK-REFERENCE.md** - Daily workflow cheat sheet
- **COMPLETE-WALKTHROUGH.md** - Full example: Digital agency platform

### Enhancements (`enhancements/`)
Optional add-ons that extend core WISC:
- Matt Pocock's requirements gathering tools (when added)
- Domain-specific patterns (when added)

### Examples (`examples/`)
Real project examples showing WISC in action (coming as builds complete)

## Daily Workflow

**Planning Session (Morning):**
```
1. /prime - Explore codebase
2. Load context if needed (.claude/context/[area].md)
3. Use sub-agents for research
4. /plan - Create implementation plan
5. Close session
```

**Implementation Session (Afternoon - NEW SESSION):**
```
1. /execute plans/[today].md
2. Build according to plan
3. Test locally
4. /commit
```

**If Long Session (>150K tokens):**
```
1. /handoff - Create transfer document
2. Close session
3. NEW session → load handoff
4. Continue work
```

## Key Principles

### 1. Separate Planning from Implementation
Never implement in the same session as planning. Plans are the ONLY context for implementation sessions (besides global rules).

### 2. Git Log = Long-Term Memory
Use `/commit` for standardized commits that track both code changes AND AI layer improvements. Future sessions read git log to catch up.

### 3. Sub-Agents for Research
Use sub-agents to explore, research, and analyze WITHOUT bloating main context. They return summaries, not full transcripts.

### 4. Just-In-Time Context Loading
Load context files only when working on that specific area. Don't load everything "just in case."

### 5. Fresh Sessions Over Compression
When context exceeds 150K tokens, use `/handoff` to transfer to fresh session rather than compressing current session.

## Stack-Specific Features

### Supabase Patterns
- Row Level Security (RLS) patterns
- Migration workflow
- Edge Functions patterns
- Realtime subscriptions
- Storage integration

### Multi-Agent Orchestration
- Task queue via Supabase tables
- Agent state management
- Handoff protocols
- VPS deployment with PM2

### VPS Deployment
- Claude Code CLI setup on Hostinger
- PM2 process management
- Long-running agent systems
- Scheduled tasks

## Token Efficiency

| Activity | Target | Max |
|----------|--------|-----|
| Planning Session | < 50K | 80K |
| Implementation | < 100K | 150K |
| Handoff Document | 3-5K | 5K |
| Commit Message | < 1K | 1K |

## Success Metrics

### Context Efficiency
- ✅ Planning sessions: < 50K tokens
- ✅ Implementation sessions: < 100K tokens
- ⚠️ Need handoff if: > 150K tokens

### Build Quality
- ✅ Clear git history (readable commits)
- ✅ Minimal hallucinations (< 5%)
- ✅ Fast iterations (plan → execute → commit)

### Agent Performance (if multi-agent)
- ✅ Task completion: > 95%
- ✅ Avg response time: < 30s
- ✅ Failed tasks: < 5%

## Use Cases

### Solo Developer
- Framework products (template systems, modules)
- Client projects (agencies, tools, platforms)
- Multi-agent systems (orchestrators, coordination)

### Agency/Consultancy
- Systematic client delivery
- Consistent build quality across projects
- Professional documentation (plans, commits)
- Easy handoff to client in-house teams

### Partnership/Collaboration
- Shared build process
- Clear communication (plans, handoffs)
- Work distribution (plans as units of work)

## Customization

### For Your Domain
1. Edit `.claude/rules.md` - Add domain patterns
2. Create `.claude/context/your-domain.md` - Domain-specific rules
3. Add skills in `.claude/skills/` - Reusable patterns
4. Build examples in `examples/` - Reference implementations

### For Your Team
1. Standardize `.claude/rules.md` - Team conventions
2. Share skill library - Common patterns
3. Review plans - Before implementation
4. Consistent commits - Team memory

## Credits

**Framework**: Based on [Cole Medin's WISC Framework](https://github.com/coleam00/context-engineering-intro)  
**Adaptation**: Janice Sommerville - JavaScript/Supabase stack, multi-agent patterns  
**Philosophy**: Template-first, capability-building approach

## License

MIT - Use freely, customize heavily, build amazing things.

## Contributing

This is a personal framework adapted for specific stack and workflow. Feel free to fork and adapt for your own needs.

## Support

- **Documentation**: See `docs/` folder for guides
- **Examples**: See `examples/` folder for real implementations (coming)
- **Issues**: File issues for bugs or unclear documentation

---

**Start your next build with WISC. Your future self will thank you.**
