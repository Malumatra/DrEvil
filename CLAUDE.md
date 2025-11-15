# CLAUDE.md - AI Assistant Guide for Dr. Evil Project

**Document Version:** 1.0
**Last Updated:** November 15, 2025
**Project Status:** Pre-Production / Planning Phase

---

## 🎯 Project Overview

**Dr. Evil** is an educational management simulation game where players command a team of skilled hacker minions who collaborate on various tasks. The game teaches professional terminology, workplace dynamics, and project management through engaging gameplay.

### Core Concept
- **Genre:** Management Simulation / Educational Game
- **Platform:** Web Browser (PC primary) with potential desktop version
- **Target Audience:** Ages 16+, students and professionals interested in tech, business, and organizational dynamics
- **Educational Goal:** Teach 100+ professional terms through natural, contextual gameplay

### Unique Value Proposition
Players learn real-world professional terminology, collaborative work patterns, and technical concepts by watching minions discuss and complete tasks - all within a fun "evil mastermind" theme.

---

## 📁 Repository Structure

### Current State (Planning Phase)
The repository is currently in the **pre-production/documentation phase**. No production code exists yet - all content is design documentation.

```
DrEvil/
├── Archive/                                    # Archived/old documentation versions
│   ├── GameDesignDocument.md
│   ├── Readme.md
│   └── gdd.md
├── dr_evil_game_design_document.md            # PRIMARY: Complete game design (753 lines)
├── dr_evil_technical_specification.md         # PRIMARY: Technical architecture (1,401 lines)
├── dr_evil_development_roadmap.md             # PRIMARY: Development plan & timeline (827 lines)
├── dr_evil_terminology_database.md            # PRIMARY: Educational content database
├── structure.md                                # Planned directory structure (aspirational)
└── CLAUDE.md                                   # This file - AI assistant guide

Future structure (not yet implemented):
├── src/                    # Source code (to be created)
│   ├── components/        # React components
│   ├── features/          # Feature modules (minions, tasks, chat, glossary)
│   ├── services/          # Business logic
│   ├── store/             # Redux state management
│   ├── types/             # TypeScript types
│   └── data/              # Static game data
├── assets/                # Images, portraits, icons (to be created)
├── tests/                 # Test files (to be created)
└── docs/                  # Additional documentation (to be created)
```

---

## 📚 Key Documentation Files

### 1. **dr_evil_game_design_document.md** - START HERE
**Purpose:** Complete game design vision and mechanics
**Read this for:**
- Game concept and premise
- Interface design and layout
- Minion system (6 types with specialties)
- Task system (categories, complexity levels)
- Educational integration approach
- Progression system and unlocks
- Sample gameplay scenarios

**Key Sections:**
- Minion Types: Infiltrator, Codebreaker, Architect, Analyst, Coordinator, Forger
- Task Categories: Research, Development, Data Operations, Documentation, Strategic Planning, Creative
- Educational Integration: How terminology learning works
- Virtual Computer System capabilities

### 2. **dr_evil_technical_specification.md**
**Purpose:** Technical implementation details and architecture
**Read this for:**
- System architecture (3-layer: Presentation, Business Logic, Data)
- Complete TypeScript data models and interfaces
- Core system algorithms (Task Generation, Assignment, Dialogue, AI)
- API specifications (internal and external)
- Performance requirements and optimization strategies
- Testing strategy and examples
- Deployment and monitoring plans

**Key Models:**
- `GameState`, `PlayerData`, `Minion`, `Task`, `ChatMessage`, `Term`, `GlossaryProgress`
- All enums: `MinionType`, `MinionStatus`, `TaskCategory`, `TaskComplexity`, `TaskStatus`

### 3. **dr_evil_development_roadmap.md**
**Purpose:** Complete development plan from concept to launch
**Read this for:**
- Development phases (0-5): Pre-Production → Foundation → Core Gameplay → Content & Polish → Testing → Launch
- Timeline: 36 weeks (9 months) to launch
- Team structure (15-17 people recommended)
- Technology stack decisions
- Risk management strategies
- Budget estimates (~$1.4M full team, $600K-$800K lean)
- Success metrics and KPIs

**Critical Path:**
Pre-production (4w) → Foundation (8w) → Core Systems (8w) → Content (8w) → Testing (6w) → Launch (2w)

### 4. **dr_evil_terminology_database.md**
**Purpose:** Complete educational content database
**Read this for:**
- Term database structure and format
- 200+ professional terms across 5 categories
- Example dialogue templates
- Task templates for content creation
- Educational progression model

**Categories:**
- Technical (API, debugging, frontend/backend, etc.)
- Business & Management (KPIs, stakeholders, ROI, etc.)
- Project Management (Agile, sprints, retrospectives, etc.)
- Collaboration & Communication (async, sync, standups, etc.)
- Professional Workplace (hierarchies, etiquette, protocols)

### 5. **structure.md**
**Purpose:** Planned directory structure (aspirational)
**Note:** This describes the FUTURE structure, not current reality. The directories described do not exist yet.

---

## 🛠️ Technology Stack

### Planned Frontend Stack
- **Framework:** React 18+ with TypeScript 5+
- **State Management:** Redux Toolkit or Zustand
- **Styling:** Tailwind CSS + CSS Modules
- **Animations:** Framer Motion
- **Build Tool:** Vite
- **Testing:** Vitest + React Testing Library

### Planned Backend (Optional)
- **Runtime:** Node.js 18+
- **Framework:** Express.js or Fastify
- **Database:** PostgreSQL or MongoDB (for cloud saves)
- **Authentication:** JWT tokens

### Development Tools
- **Version Control:** Git
- **Code Quality:** ESLint + Prettier
- **CI/CD:** GitHub Actions
- **Deployment:** Vercel/Netlify (web), Electron (desktop)

---

## 🎮 Core Game Systems

### 1. Minion System
Six distinct minion types, each with:
- Unique specialties and skills
- Personality traits affecting collaboration
- Energy/morale mechanics
- Relationship web with other minions
- Progressive skill development

**Minion Types:**
1. **Infiltrator** - Research, OSINT, social engineering
2. **Codebreaker** - Software development, hacking
3. **Architect** - System design, infrastructure
4. **Analyst** - Data analysis, intelligence
5. **Coordinator** - Project management, organization
6. **Forger** - Documentation, creative content

### 2. Task System
Tasks are the core gameplay loop:
- Player assigns tasks via text input
- Minions collaborate and discuss approach
- Educational terms appear in natural conversation
- Deliverables produced (reports, code, documents)
- Rewards earned (EEP, experience, unlocks)

**Complexity Levels:**
- Simple: 1 minion, 1-5 min, basic terms
- Standard: 1-2 minions, 5-15 min, intermediate
- Complex: 2-4 minions, 15-30 min, advanced
- Epic: 3-6 minions, 30+ min, full lifecycle

### 3. Educational System
- Terms highlighted in minion conversations
- Hover tooltips for definitions
- Glossary building and mastery tracking
- Spaced repetition for retention
- Adaptive difficulty based on progress

### 4. Collaboration Engine
Minions simulate realistic teamwork:
- Planning discussions
- Work progress updates
- Peer review and feedback
- Problem-solving brainstorms
- Retrospectives

---

## 💡 Development Conventions

### Code Style (When Implementation Begins)
```typescript
// Use TypeScript for all code
// Functional components with hooks (React)
// PascalCase for components: TaskCard, MinionPortrait
// camelCase for functions: calculateScore, generateDialogue
// UPPER_SNAKE_CASE for constants: MAX_MINIONS, DEFAULT_ENERGY
// Interfaces: PascalCase (Task, GameState)
```

### File Naming
- Components: `PascalCase.tsx` (e.g., `MinionGallery.tsx`)
- Utilities: `camelCase.ts` (e.g., `calculations.ts`)
- Tests: `*.test.ts` or `*.spec.ts`
- Data files: `camelCase.json` (e.g., `terminology.json`)

### Git Workflow
- Main branch: `main` (or as specified in git config)
- Feature branches: Descriptive names (e.g., `feature/minion-ai-system`)
- Commit messages: Clear, descriptive, following conventional commits
- Pull requests: Required for major changes

### Testing Requirements
- Unit tests for all business logic
- Integration tests for system interactions
- E2E tests for critical user journeys
- Performance tests for optimization validation
- Target: >80% code coverage

---

## 🎯 AI Assistant Guidelines

### When Working on This Project

#### 1. **Understand Current Phase**
This project is in **pre-production**. There is NO production code yet. All work is documentation and planning.

**DO:**
- Read the design documents thoroughly before implementing
- Reference the technical specification for data models
- Follow the planned architecture exactly
- Create files according to the planned structure
- Maintain consistency with design decisions

**DON'T:**
- Assume code exists when it doesn't
- Deviate from documented architecture without discussion
- Create alternative structures - follow the plan
- Skip reading the specification documents

#### 2. **Documentation is Source of Truth**
The four main documentation files are the authoritative reference:
- Game Design Document = "What" we're building
- Technical Specification = "How" we're building it
- Development Roadmap = "When" and "Who"
- Terminology Database = Educational content

**When in doubt:**
1. Check the Game Design Document for feature intent
2. Check the Technical Specification for implementation details
3. Check the Roadmap for priorities and dependencies

#### 3. **Implementing Features**

**Before coding ANY feature:**
1. Read relevant sections in Game Design Document
2. Review data models in Technical Specification
3. Check if dependencies exist (see Roadmap Phase descriptions)
4. Verify planned directory structure
5. Create necessary directories if they don't exist

**Example: Implementing Minion System**
```
1. Read: GDD "Minion System" section (lines 93-138)
2. Review: Tech Spec "Minion Model" (lines 168-228)
3. Check: Roadmap Week 9-10 dependencies
4. Create: src/features/minions/ directory structure
5. Implement: Following exact TypeScript interfaces
6. Test: According to testing strategy (Tech Spec lines 1028-1158)
```

#### 4. **Creating New Content**

**For Tasks:**
- Follow task template format in Terminology Database
- Match complexity to player level guidelines
- Include 2-4 educational terms per task
- Write natural dialogue showing collaboration
- Create appropriate deliverables

**For Terminology:**
- Use exact JSON schema from Terminology Database
- Categorize correctly (technical, business, project_mgmt, collaboration, professional)
- Set appropriate difficulty level
- Write 2+ example usages
- Link related terms

#### 5. **Code Organization**

When creating production code:

```typescript
// 1. Import order
import React from 'react';                    // External dependencies
import { useSelector } from 'react-redux';    // State management
import { MinionCard } from '@/components';    // Internal components
import { Minion } from '@/types';            // Types
import { calculateScore } from '@/utils';     // Utilities

// 2. Type definitions
interface MinionGalleryProps {
  minions: Minion[];
  onSelect: (id: string) => void;
}

// 3. Component
export const MinionGallery: React.FC<MinionGalleryProps> = ({ minions, onSelect }) => {
  // Implementation
};
```

#### 6. **Common Tasks Reference**

| Task | Location | Key Info |
|------|----------|----------|
| Add new minion type | GDD lines 96-122, Tech Spec lines 212-219 | Follow existing pattern |
| Create task | Terminology DB section 7, Tech Spec lines 444-477 | Use TaskGenerator class |
| Add terminology | Terminology DB section 1 | Use exact JSON schema |
| Implement UI component | GDD lines 28-92, Tech Spec file structure | Follow component patterns |
| Write dialogue | Terminology DB section 8, Tech Spec lines 534-582 | Use DialogueGenerator |

#### 7. **What NOT to Do**

**AVOID:**
- Creating code without reading specifications first
- Changing core data models (they're finalized)
- Adding features not in Game Design Document
- Skipping TypeScript types (everything is typed)
- Ignoring educational aspect (it's core to the game)
- Creating monolithic files (follow modular structure)
- Hardcoding values (use configuration)

**If you need to deviate:**
1. Explain why the documented approach won't work
2. Propose alternative with justification
3. Get approval before proceeding

#### 8. **Testing Your Work**

Every implementation should include:
```typescript
// Example test structure
describe('MinionAI', () => {
  describe('generateDialogue', () => {
    it('should include personality traits', () => {
      // Test implementation
    });

    it('should inject appropriate terminology', () => {
      // Test implementation
    });
  });
});
```

Refer to Tech Spec lines 1028-1158 for testing patterns.

---

## 🔍 Quick Reference

### Finding Information

| Need to know... | Check... | Section/Lines |
|----------------|----------|---------------|
| What minions can do | Game Design Document | Lines 96-138 |
| Minion data structure | Technical Specification | Lines 168-228 |
| Task categories | Game Design Document | Lines 142-186 |
| Task data model | Technical Specification | Lines 231-295 |
| How dialogue works | Technical Specification | Lines 534-582 |
| Educational system | Game Design Document | Lines 196-243 |
| Terminology format | Terminology Database | Lines 24-44 |
| Development timeline | Development Roadmap | Lines 541-572 |
| Technology choices | Technical Specification | Lines 74-123 |
| Testing strategy | Technical Specification | Lines 1028-1158 |

### Key Metrics & Targets

**Performance:**
- Initial Load: <3 seconds
- Save Game: <500ms
- Chat Message Render: <16ms (60fps)
- Memory: <200MB RAM

**Gameplay:**
- Session length target: 20+ minutes
- Tasks per session: 3-5
- Terms encountered: 5-10 per session
- Terms mastered: 2-3 per hour of play

**Quality:**
- Test coverage: >80%
- Error rate: <1%
- 1-day retention: 60%
- 7-day retention: 40%

---

## 🚀 Getting Started (Implementation Phase)

### For AI Assistants Beginning Implementation

1. **First-Time Setup**
```bash
# When code implementation begins:
npm create vite@latest dr-evil -- --template react-ts
cd dr-evil
npm install

# Install dependencies per Tech Spec lines 480-495
npm install react@18 react-dom@18
npm install @reduxjs/toolkit react-redux
npm install framer-motion tailwindcss
# ... (see full list in roadmap)
```

2. **Project Structure Creation**
```bash
# Create directories per structure.md
mkdir -p src/{components,features,services,store,hooks,utils,types,data,assets}
mkdir -p src/features/{minions,tasks,chat,glossary}
mkdir -p assets/{images,sounds}
mkdir -p assets/images/{minion_portraits,ui}
mkdir -p tests
```

3. **First Implementation: Core Data Models**
- Start with: `src/types/` directory
- Implement interfaces from Tech Spec lines 131-438
- Create: `GameState.ts`, `Minion.ts`, `Task.ts`, `Chat.ts`, `Terminology.ts`

4. **Development Workflow**
```bash
# Daily workflow (when in development):
npm run dev          # Start development server
npm run test         # Run tests
npm run lint         # Check code quality
npm run type-check   # TypeScript validation
```

---

## 📋 Development Phases & Priorities

### Current Phase: Phase 0 - Pre-Production ✅
**Status:** Documentation complete
**Next:** Secure team/funding, begin Phase 1

### Phase 1: Foundation (Weeks 5-12)
**Priority Implementation Order:**
1. Game state management system (Week 5-6)
2. UI Framework and components (Week 7-8)
3. Minion system (Week 9-10)
4. Task system basics (Week 11-12)

### What to Build First (When Implementation Starts)
1. Core data models (TypeScript interfaces)
2. State management setup (Redux store)
3. Basic UI layout (Dashboard skeleton)
4. Minion card component
5. Simple task assignment flow
6. Chat message display

**Dependencies Matter:** Check Roadmap lines 565-571 for implementation order dependencies.

---

## 🎨 Visual & UX Guidelines

### Color Scheme
- Primary: Dark blue/purple (evil lair aesthetic)
- Accent: Electric green/cyan (tech/hacker feel)
- Neutral: Grays for backgrounds
- Alerts: Red (urgent), Yellow (warnings), Green (success)

### Component Patterns
All components should:
- Be fully typed (TypeScript)
- Support dark theme
- Be keyboard accessible
- Include loading states
- Handle errors gracefully
- Support responsive design

### Accessibility Requirements
- Adjustable font sizes
- Color blind friendly palettes
- Full keyboard navigation
- Screen reader compatible
- WCAG 2.1 AA compliance

---

## 🐛 Common Issues & Solutions

### Issue: "Where's the code?"
**Solution:** Project is in planning phase. Code doesn't exist yet. Start with Phase 1 tasks from Roadmap.

### Issue: "Data model doesn't match my needs"
**Solution:** Data models are finalized in Tech Spec. Don't change them without very strong justification. They're designed to support all planned features.

### Issue: "Can I use a different technology?"
**Solution:** Tech stack is decided (React, TypeScript, Redux/Zustand, Tailwind). Changing requires discussion of trade-offs.

### Issue: "Documentation conflicts"
**Solution:** Technical Specification > Game Design Document > Roadmap for technical decisions. Game Design Document > Technical Specification for feature intent.

### Issue: "Should I implement feature X?"
**Solution:** Check if it's in Game Design Document. If yes and you're past dependencies, proceed. If no, it's probably "Phase 2+" - log as future enhancement.

---

## 📞 Questions to Ask Users

### Before Starting Major Work

1. "Have you reviewed the [relevant design doc section]? I want to ensure my implementation matches your vision."

2. "The specification shows [X approach]. Is this still the preferred method, or have you changed direction?"

3. "I notice [Y dependency] needs to be completed first. Should I implement that first, or is it already done?"

4. "The planned structure shows [Z]. Do you want me to create this exactly as documented?"

### During Implementation

1. "I'm seeing [potential issue] with the documented approach. Can we discuss alternatives?"

2. "Do you want me to implement the full [system] or create an MVP version first for testing?"

3. "Should I create placeholder content or wait for the content team's work?"

---

## 🎓 Educational Philosophy

**Critical to understand:** This is not just a game. It's an educational tool disguised as a game.

### Educational Goals Come First
- Every task must teach terminology naturally
- Dialogue must sound professional AND educational
- Players should learn without feeling "taught"
- Terms appear in realistic work contexts

### Content Quality Standards
- Terminology definitions must be accurate
- Example usage must be authentic to professional contexts
- Dialogue must reflect real workplace collaboration
- Tasks must simulate actual work scenarios

### Learning Mechanics
- Contextual introduction (terms highlighted)
- Spaced repetition (terms reappear)
- Progressive difficulty (beginner → expert)
- Active application (use terms in later tasks)

**When creating ANY content, ask:** "Does this teach something valuable in an engaging way?"

---

## 🔄 Version Control & Branching

### Branch Strategy
- `main` - Production-ready code
- `develop` - Integration branch
- `feature/*` - Feature branches
- `bugfix/*` - Bug fix branches
- `hotfix/*` - Critical fixes

### Commit Message Format
```
type(scope): subject

body (optional)

footer (optional)
```

**Types:** feat, fix, docs, style, refactor, test, chore

**Examples:**
```
feat(minions): implement Codebreaker AI personality
fix(tasks): correct task completion calculation
docs(readme): update installation instructions
```

---

## 📊 Success Metrics to Track

### During Development
- Story points completed per week
- Test coverage percentage
- Bug resolution rate
- Code review turnaround time

### Post-Launch
- Average session length (target: 20+ min)
- Terms learned per session (target: 5-10)
- Task completion rate
- User retention (1-day: 60%, 7-day: 40%)

---

## 🎯 Final Checklist for AI Assistants

Before implementing ANY feature:

- [ ] Read relevant Game Design Document section
- [ ] Review Technical Specification data models
- [ ] Check Roadmap for phase and dependencies
- [ ] Verify no existing implementation
- [ ] Create necessary directory structure
- [ ] Follow TypeScript interfaces exactly
- [ ] Include educational component (if applicable)
- [ ] Write tests alongside code
- [ ] Follow code style conventions
- [ ] Update documentation if needed

---

## 📝 Document Maintenance

### When to Update This File
- Major architectural changes
- New phases or features added
- Technology stack changes
- Directory structure modifications
- New conventions established

### Update Process
1. Modify CLAUDE.md
2. Update version number and date at top
3. Note changes in commit message
4. Notify team of significant changes

---

## 🙋 Need Help?

### Key Resources
1. **Design Questions:** Check Game Design Document
2. **Technical Questions:** Check Technical Specification
3. **Timeline Questions:** Check Development Roadmap
4. **Content Questions:** Check Terminology Database

### If Documentation Doesn't Answer Your Question
1. Check if it's a Phase 2+ feature (out of scope)
2. Review related systems for context
3. Ask specific questions referencing doc sections
4. Propose solutions based on existing patterns

---

## 📚 Appendix: File Line References

### Quick Navigation by Line Numbers

**Game Design Document (753 lines total)**
- Executive Summary: 1-10
- Interface Design: 28-92
- Minion System: 93-138
- Task System: 142-193
- Educational Integration: 196-243
- Collaboration System: 247-288
- Progression System: 292-341
- Tutorial & Onboarding: 509-544
- Sample Gameplay Scenario: 423-451

**Technical Specification (1,401 lines total)**
- System Architecture: 23-73
- Technology Stack: 74-123
- Data Models: 126-438
- Core Systems: 442-788
- API Specifications: 790-880
- Performance Requirements: 883-933
- Testing Strategy: 1028-1158
- Deployment: 1162-1247

**Development Roadmap (827 lines total)**
- Project Overview: 21-52
- Development Phases: 56-430
- Team Structure: 433-474
- Milestones & Timeline: 541-572
- Risk Management: 575-650
- Budget Estimate: 653-702
- Success Metrics: 705-756

---

**End of CLAUDE.md**

---

## Meta Information

**File Purpose:** Comprehensive guide for AI assistants working on Dr. Evil project
**Intended Audience:** Claude, GitHub Copilot, and other AI coding assistants
**Maintenance:** Update when major project changes occur
**Related Files:** All primary documentation files listed above

**Pro Tip for AI Assistants:** When uncertain about ANYTHING, it's better to ask than to assume. This project has detailed specifications for a reason - follow them closely for best results.
