

# TL;DR: Development Workflow Process

## The 4-Phase Approach

**ANALYZE → PLAN → EXECUTE → TEST → DONE**

---

## Quick Overview

### 🔍 **Phase 1: ANALYZE** 
**Stop and Ask Questions**
- Understand requirements
- Review existing code
- **Ask clarifying questions**
- ⚠️ **WAIT for answers before continuing**

### 📋 **Phase 2: PLAN**
**Create `.plan/{feature-name}/` with:**
- `implementation-plan.md` - Strategy & steps
- `checklist.md` - Trackable tasks
- `solution-description.md` - Design decisions
- `.mermaid` files - Visual diagrams
- Create feature branch: `feature/{id}_{name}`

### ⚙️ **Phase 3: EXECUTE**
**Code while tracking progress:**
- Follow the plan
- Check off items in `checklist.md` as you go
- Commit logical units
- No TODOs in production code

### ✅ **Phase 4: TEST**
**Verify everything:**
- Build succeeds
- All tests pass (old + new)
- No warnings in new code
- No TODOs remain

---

## Key Rules

1. **Never skip ANALYZE** - Always ask questions first
2. **Update checklist in real-time** - Not at the end
3. **Definition of Done is mandatory** - All criteria must be met
4. **Quality over speed** - Don't compromise standards

---

## In One Sentence

**Analyze & ask questions → Plan in `.plan/` directory → Execute while checking off tasks → Test everything before calling it done.**