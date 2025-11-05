# Demo Scope - Innovation Lifecycle Manager

## Overview

This document defines the **minimum viable demo** that can be built in a few hours to demonstrate the core concept of the Innovation Lifecycle Manager.

**Target Build Time**: 4-6 hours
**Target Demo Duration**: 10-15 minutes

---

## Demo Objectives

1. Show how ideas are submitted and appear on a Kanban board
2. Demonstrate lifecycle progression through stages
3. Showcase one AI feature (duplicate detection)
4. Prove the concept is viable for further investment

---

## Simplified Lifecycle Stages (Demo Only)

Instead of 9 stages, use **4 stages** for the demo:

1. **Idea** - Initial submission
2. **Concept** - Being evaluated
3. **Development** - Being built (combines POV/Prototype/POC)
4. **Deployed** - Live in production (combines Pilot/Product/Scaled)

---

## Demo Epics & User Stories

### Epic 1: Basic Authentication (1 hour)
**Goal**: Simple login to identify users

**Stories**:
- DS1: As a user, I can log in with email/password
- DS2: As a user, I see my name displayed after login

**Implementation**:
- Hard-coded users (no database needed for demo)
- Simple session management
- 3 test users: Employee, Reviewer, Admin

---

### Epic 2: Idea Submission (1 hour)
**Goal**: Submit basic innovation ideas

**Stories**:
- DS3: As an employee, I can submit a new idea with title, description, and category
- DS4: As an employee, I see confirmation after submission

**Implementation**:
- Simple form with 4 fields: Title, Description, Category, Problem Statement
- Categories: Technology, Process, Product, Other
- Store in local storage or simple JSON file for demo

---

### Epic 3: Kanban Board (1.5 hours)
**Goal**: Visualize ideas across lifecycle stages

**Stories**:
- DS5: As a user, I see a Kanban board with 4 columns (stages)
- DS6: As a user, I see initiative cards showing title, owner, and category
- DS7: As a user, I can click a card to see full details

**Implementation**:
- Simple 4-column layout
- Cards show: title, owner name, category badge
- Modal or side panel for details
- No drag-and-drop (too complex for time constraint)

---

### Epic 4: Simple Lifecycle Progression (1 hour)
**Goal**: Move initiatives through stages

**Stories**:
- DS8: As an owner, I can request to move my initiative to the next stage
- DS9: As a reviewer, I can approve or reject stage transitions
- DS10: As a user, I see the initiative move to the new stage after approval

**Implementation**:
- Simple "Request Next Stage" button on initiative detail
- Reviewer sees "Pending Approvals" list
- One-click approve/reject (no detailed workflow)
- Status updates immediately

---

### Epic 5: AI Duplicate Detection (1.5 hours)
**Goal**: Demonstrate AI value with one killer feature

**Stories**:
- DS11: As a user submitting an idea, the system checks for similar ideas
- DS12: As a user, I see a warning if similar ideas exist before I submit

**Implementation**:
- Call Claude API during submission
- Simple semantic similarity check against existing ideas
- Show list of similar ideas with similarity score
- User can proceed anyway or cancel

---

## Out of Scope for Demo

**Explicitly NOT included to save time**:

❌ Multiple user roles (just simulate with hardcoded flag)
❌ Comments and collaboration
❌ Attachments
❌ Analytics and reporting
❌ Notifications
❌ Search functionality (beyond basic filter)
❌ Audit trail
❌ Advanced AI features (improvement suggestions, Q&A, etc.)
❌ Metrics tracking
❌ User management
❌ Status management (On Hold, Cancelled, etc.)
❌ Stage-specific requirements validation
❌ Email notifications
❌ Export capabilities
❌ Mobile responsiveness (desktop only for demo)

---

## Demo Data

**Pre-populate with 10-15 sample initiatives** across the 4 stages:
- 4 in Idea stage
- 3 in Concept stage
- 3 in Development stage
- 2 in Deployed stage
- 1 pending approval (to demo workflow)

**Categories**:
- Technology Innovation
- Process Improvement
- Product Development
- Other

---

## Technology Stack (Simplified)

**Frontend**:
- HTML/CSS/JavaScript (vanilla or simple framework like Alpine.js)
- OR: React if you're comfortable (create-react-app)
- Tailwind CSS for quick styling

**Backend**:
- Node.js + Express (minimal API)
- OR: Python + Flask
- JSON file for data storage (no database)

**AI**:
- Direct calls to Anthropic Claude API
- Simple prompt engineering

**Deployment** (for demo):
- Run locally (no deployment needed)
- OR: Quick deploy to Vercel/Netlify if want to share

---

## Demo Flow (15 minutes)

### Part 1: Idea Submission (3 min)
1. Log in as Employee
2. Submit a new idea: "AI-Powered Meeting Scheduler"
3. AI detects similarity to existing "Calendar Integration" idea
4. Show warning, proceed anyway
5. Idea appears on board in "Idea" stage

### Part 2: Lifecycle Progression (4 min)
6. Log in as Reviewer
7. View pending approvals
8. Approve the new idea to move to "Concept"
9. Show it moving on the Kanban board
10. Click to view full details

### Part 3: AI Feature (3 min)
11. Submit another idea: "Smart Calendar Assistant"
12. AI detects high similarity (>70%) to the just-submitted idea
13. Shows detailed comparison
14. Demonstrates AI value

### Part 4: Board Overview (3 min)
15. Show full Kanban board with all initiatives
16. Filter by category
17. Show different stages
18. Discuss future vision

### Part 5: Q&A (2 min)

---

## Success Criteria

The demo is successful if:
✅ User can submit an idea in under 30 seconds
✅ Kanban board clearly shows innovation pipeline
✅ Stage progression workflow is clear and functional
✅ AI duplicate detection impresses audience ("wow moment")
✅ Stakeholders can envision the full product

---

## Development Sequence

### Hour 1: Setup & Foundation
- Project setup
- Basic routing/navigation
- Login page (hardcoded users)
- Home page with Kanban board scaffold

### Hour 2: Kanban Board
- 4-column layout
- Display sample data
- Card components
- Click to view details modal

### Hour 3: Idea Submission
- Submission form
- Form validation
- Add to board
- Success confirmation

### Hour 4: AI Integration
- Claude API setup
- Duplicate detection logic
- Similarity checking
- Warning display

### Hour 5: Lifecycle Progression
- Request stage transition button
- Approval interface for reviewer
- Update board state
- Status updates

### Hour 6: Polish & Demo Data
- Add sample initiatives
- Styling improvements
- Test demo flow
- Fix bugs
- Prepare demo script

---

## Technical Simplifications

To save time:

1. **No Database**: Use JSON file or local storage
2. **No Real Auth**: Hardcode 3 users, simple login form
3. **No API Middleware**: Direct function calls
4. **Minimal Validation**: Basic field checks only
5. **No Error Handling**: Happy path only for demo
6. **Simple Styling**: Use Tailwind or basic CSS framework
7. **No Tests**: Manual testing only
8. **No State Management**: Simple component state
9. **No Build Optimization**: Development mode only
10. **Desktop Only**: Don't worry about mobile

---

## What We're Proving

This minimal demo proves:
✅ The concept is sound
✅ The workflow makes sense
✅ AI can add real value
✅ Users can understand it immediately
✅ It's worth investing in full development

---

## Next Steps After Demo

If demo is successful:
1. Gather feedback
2. Refine requirements based on reactions
3. Plan proper development phases
4. Add back features from full scope
5. Build production-ready version

---

## Estimated Total Time

| Activity | Time |
|----------|------|
| Setup & Auth | 1 hour |
| Kanban Board | 1.5 hours |
| Idea Submission | 1 hour |
| AI Integration | 1.5 hours |
| Lifecycle Progression | 1 hour |
| Polish & Testing | 1 hour |
| **Total** | **7 hours** |

*Note: Can be compressed to 4-6 hours if you skip polish and use pre-built components*

---

## Critical Path

**Absolute must-haves** (can demo without anything else):
1. Login (even fake)
2. Kanban board showing initiatives
3. Submit new idea
4. AI duplicate detection

**Nice-to-haves** (add if time permits):
5. Stage progression workflow
6. Filter by category
7. Better styling

---

*Last Updated: Demo Scope Definition*
*Status: Ready for Development*
