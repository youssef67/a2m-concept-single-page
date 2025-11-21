---
description: EPCT workflow - Explore, Plan, Code, Test
argument-hint: <feature description>
tags: [workflow, development]
---

# EPCT: $ARGUMENTS

Execute feature using **Explore → Plan → Code → Test** methodology.

---

## 🔍 EXPLORE

**Goal:** Gather sufficient context before making any decisions.

### External Research (if needed)
- [ ] Use WebSearch for relevant docs, patterns, gotchas, best practices
- [ ] Research design inspiration (if UI work)
- [ ] Check framework/library documentation

### Codebase Analysis
- [ ] Use Task tool (`subagent_type=Explore`) to find:
  - Similar existing features
  - Established patterns
  - Files that will be affected
- [ ] Read configuration files:
  - `package.json` (available scripts, dependencies)
  - Framework configs (`astro.config.mjs`, `tsconfig.json`, etc.)
  - Styling configs (`tailwind.config.mjs`, etc.)
- [ ] Review `CLAUDE.md` for project-specific guidelines and constraints
- [ ] Identify design system components (if applicable)

### Project-Specific Checks (A2M Vitrine)
- [ ] **Mobile-first constraint**: How will this look on mobile first?
- [ ] **Tailwind only**: Can this be done with Tailwind utilities?
- [ ] **Performance**: Impact on load time / bundle size?
- [ ] **Astro patterns**: Does this follow Astro best practices (islands, SSG)?

### Stop Condition
⚠️ **DO NOT PROCEED** until context is sufficient to make informed decisions.

---

## 📝 PLAN

**Goal:** Design a clear, approved solution before writing code.

### Create Comprehensive Plan

**1. Key Findings from Exploration**
- Summarize relevant patterns discovered
- Note potential conflicts or challenges
- Identify reusable components/utilities

**2. Files to Modify/Create**
- List all affected files
- Specify new files to create
- Note any files to delete

**3. Implementation Steps**
- Break down into logical, sequential steps
- Estimate complexity/time per step
- Identify dependencies between steps

**4. Testing Approach**
- What existing tests will validate this?
- How to manually test on mobile/desktop?
- Performance validation strategy

### Self-Challenge Questions
- **Assumptions**: What am I assuming? Are they valid?
- **Alternatives**: Are there multiple approaches? Which fits best?
- **Uncertainties**: What don't I know? What could go wrong?
- **Breaking Changes**: Will this break existing functionality?
- **Mobile-First**: Did I design for mobile FIRST?

### Present Plan via AskUserQuestion

**Format:**
```
# Proposed Plan for [Feature]

## Context
[Brief summary of exploration findings]

## Approach
[Chosen solution and why]

## Files
- Create: [list]
- Modify: [list]

## Steps
1. [Step 1]
2. [Step 2]
...

## Uncertainties
- [Any questions or concerns]

## Alternatives Considered
- [Other approaches and why not chosen]

Do you approve this plan?
```

### ⚠️ CRITICAL STOP POINT

**DO NOT WRITE CODE WITHOUT EXPLICIT APPROVAL**

Wait for user to:
- ✅ Approve the plan, OR
- 🔄 Request modifications, OR
- ❌ Reject and request new approach

---

## 💻 CODE

**Goal:** Execute ONLY the approved plan.

### Pre-Coding Setup
- [ ] Use `TodoWrite` to create checklist from approved plan steps
- [ ] Review approved plan one more time

### During Implementation
- [ ] Follow approved plan strictly
- [ ] Use established patterns from codebase
- [ ] Respect project constraints (mobile-first, Tailwind-only, etc.)
- [ ] Make atomic commits (1 logical change = 1 commit)
- [ ] Write clear commit messages

### If Issues Arise
**STOP and ask** if:
- Plan doesn't work as expected
- Need to deviate from approved approach
- Discover new information that changes the solution
- Face unexpected technical limitations

**DO NOT** improvise solutions without approval.

---

## ✅ TEST

**Goal:** Validate implementation with existing infrastructure.

### Discover Available Tests

**Read `package.json` scripts:**
```json
{
  "scripts": {
    "dev": "...",
    "build": "...",
    "lint": "...",     // ← Check if exists
    "test": "...",     // ← Check if exists
    "check": "..."     // ← Type checking
  }
}
```

**Look for config files:**
- Lint: `.eslintrc`, `eslint.config.js`
- Types: `tsconfig.json`
- Tests: `vitest.config.js`, `jest.config.js`

### Run ONLY Existing Commands

**In this order:**

1. **Type Check** (if TypeScript)
```bash
   npm run astro check  # or npm run type-check
```

2. **Lint** (if configured)
```bash
   npm run lint
```

3. **Tests** (if test suite exists)
```bash
   npm run test
```

4. **Build**
```bash
   npm run build
```
   - Must succeed without errors
   - Check for warnings

5. **Manual Testing**
   - [ ] Test on mobile viewport (< 768px)
   - [ ] Test on tablet viewport (768px - 1024px)
   - [ ] Test on desktop viewport (> 1024px)
   - [ ] Verify all interactive elements work
   - [ ] Check accessibility (keyboard navigation, focus)
   - [ ] Test form submissions (if applicable)

### Fix All Issues

- [ ] Fix all TypeScript errors
- [ ] Fix all lint warnings/errors
- [ ] Fix failing tests
- [ ] Fix build errors
- [ ] Resolve any manual test issues

### Project-Specific Validation (A2M Vitrine)

- [ ] **Mobile-first check**: Does it look perfect on mobile?
- [ ] **Touch targets**: Are buttons 44x44px minimum?
- [ ] **Font sizes**: Minimum 16px for body text?
- [ ] **Performance**: Run Lighthouse (target > 90)
- [ ] **Images**: Optimized and lazy-loaded?
- [ ] **No horizontal scroll**: On any viewport size?

### Important Restrictions

**DO NOT:**
- ❌ Create new test files (unless explicitly requested)
- ❌ Run non-existent commands
- ❌ Install testing tools without approval
- ❌ Skip validation steps

---

## 📊 EPCT Summary
```
┌─────────────────────────────────────────────────────────┐
│  E - EXPLORE                                            │
│  └─> Gather context, research, analyze codebase        │
│                                                         │
│  P - PLAN                                               │
│  └─> Design solution, get approval [⚠️ STOP HERE]     │
│                                                         │
│  C - CODE                                               │
│  └─> Implement approved plan only                      │
│                                                         │
│  T - TEST                                               │
│  └─> Validate with existing tools + manual tests       │
└─────────────────────────────────────────────────────────┘
```

---

**Starting EXPLORE phase for:** $ARGUMENTS
```

---

## 📊 Résumé des Changements

### `claude.md` - Contexte Projet
✅ **Garde :**
- Vue d'ensemble du projet
- Stack technique
- Contraintes mobile-first (SPÉCIFIQUES au projet)
- Charte graphique (couleurs, typo, espacements)
- Structure du site (sections)
- Architecture de fichiers
- Commandes de développement
- Checklist de validation (SPÉCIFIQUE au projet)
- Principes de développement

❌ **Supprime :**
- Explication détaillée du workflow EPCT (→ dans epct.md)
- Steps détaillées E/P/C/T (→ dans epct.md)

### `epct.md` - Méthodologie Pure
✅ **Garde :**
- Workflow EPCT générique et réutilisable
- Checklist détaillée pour chaque phase
- Instructions step-by-step
- Questions de validation

✅ **Ajoute :**
- Checks spécifiques au projet dans les sections appropriées
- Référence au mobile-first dans EXPLORE
- Validation mobile dans TEST

---

## 🎯 Usage

### Démarrage avec Claude Code
```
Claude, lis claude.md et commands/epct.md.

Feature: Créer le composant Hero.astro avec titre, CTA et image de fond.

Démarre la phase EXPLORE.