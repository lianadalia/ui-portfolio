# UI Portfolio

A collection of high-fidelity HTML/CSS UI mockups covering six design domains: user & group management, browser chrome, mobile wellness app, QA test dashboard, social profile, and personal journaling. All screens are captured into a single Figma file alongside full UX documentation (site map, user flows, navigation flow).

---

## Overview

This portfolio demonstrates end-to-end UI design thinking — from information architecture through interaction flows to pixel-level screen design. Each section tackles a different product context and design challenge, showing range across admin tools, consumer apps, and developer tooling.

**[▶ Interactive Prototype](http://localhost:8765/prototype.html)** — click through 4 flows (Admin: Manage a User, Create a Group, Reveal Hidden Group, Editor: Check Permissions). Serve locally first — see [Live Demo](#live-demo) below.

---

## Key Features

### User & Group Management Tool
A full-featured admin panel for managing editors, groups, and permissions inside a content platform.

- **Editors View** — Grid of editor cards with role/status filters and a slide-in detail panel showing permissions, group memberships, and recent activity
- **Hidden Groups** — Admin-only list of visibility-restricted groups with access rules, audit controls, and a one-click reveal workflow
- **Group Creation** — 4-step wizard (Basics → Settings → Members → Permissions) with icon picker, colour selector, parent group dropdown, and visibility radio options
- **Group Inspection** — Group hero strip with live stats, tabbed members table, sub-group cards, and inherited permission toggles
- **User Management** — Paginated user table with 5 stat cards (total / active / pending / suspended / MFA %), filter chips, bulk action bar, and per-row quick actions
- **User Inspection** — 3-column user profile: identity + active sessions | effective permissions grid + group memberships | 30-day audit log timeline

### Browser
macOS-style browser chrome mockup with tab bar (5 tabs), address bar with security indicator, bookmarks bar, and a fully rendered fictional website (NovaSphere) inside the viewport.

### Mobile App — Bloom Wellness
Three iPhone mockups side-by-side showing a wellness tracking app:
- Home/Dashboard with daily summary cards
- Progress screen with weekly charts
- Mood check-in screen with emoji selector and journaling prompt

### Test Dashboard
Dark-theme QA tool for a software team:
- Stats row: 128 tests · 76 passed · 4 failed · 48 skipped
- Test suite list with pass/fail/skip status rows
- Expandable error detail panel with stack trace and diff view

### Profile
Light-theme social profile page with cover photo, avatar, skill proficiency bars, activity feed posts, and achievement badge grid.

### Self-Reflection Journal
Warm minimal journaling interface with serif typography:
- Entry sidebar with past entries and mood indicators
- Writing area with guided prompts
- Insights panel showing mood trend chart and streak counter

---

## Live Demo

Serve locally with Node.js (no install required):

```bash
node -e "
const http=require('http'),fs=require('fs'),path=require('path');
http.createServer((req,res)=>{
  const f=path.join('.',req.url==='/'?'/cover.html':req.url);
  fs.readFile(f,(e,d)=>{
    if(e){res.writeHead(404);res.end();}
    else{res.writeHead(200,{'Content-Type':req.url.endsWith('.html')?'text/html':'text/plain'});res.end(d);}
  });
}).listen(8765,()=>console.log('Open http://localhost:8765'));
"
```

Then open **http://localhost:8765** — this loads `cover.html`, the portfolio hub with navigation to all screens.

| Screen | URL |
|---|---|
| Portfolio Cover | `/cover.html` |
| Editors View | `/editors-view.html` |
| Hidden Groups | `/hidden-groups.html` |
| Group Creation | `/group-creation.html` |
| Group Inspection | `/group-inspection.html` |
| User Management | `/user-management2.html` |
| User Inspection | `/user-inspection.html` |
| Browser | `/browser.html` |
| Mobile App | `/mobile-app.html` |
| Test Dashboard | `/test-dashboard.html` |
| Profile | `/profile.html` |
| Self-Reflection | `/self-reflection.html` |

---

## Figma Mockups

All screens are captured in a single Figma file:

**[View in Figma →](https://www.figma.com/design/EKIq2WVI6GUUhGfBjalV9i)**

| Screen | Node |
|---|---|
| Editors View | `9:2` |
| Hidden Groups | `10:2` |
| Group Creation | `11:2` |
| Group Inspection | `12:2` |
| User Management | `13:2` |
| User Inspection | `14:2` |

---

## Figma Flows

UX documentation is captured in the same Figma file:

| Document | Node | Description |
|---|---|---|
| **Site Map** | `19:2` | Full IA tree — all 6 sections and their sub-screens |
| **User Flow** | `20:2` | 4 key interaction paths for Admin and Editor roles |
| **Navigation Flow** | `21:2` | Screen-to-screen navigation diagram with primary, back, and in-section links |

### Site Map

![Site Map](docs/sitemap.png)

### User Flow

![User Flow](docs/user-flow.png)

### Navigation Flow

![Navigation Flow](docs/navigation-flow.png)

### User Flows covered

1. **Admin: Manage a User** — Cover → User Management → search → User Inspection → Edit Role / Suspend / Add to Group
2. **Admin: Create a Group** — Groups list → Group Creation wizard (4 steps) → Group Inspection
3. **Admin: Reveal a Hidden Group** — Hidden Groups → select → Make Visible → confirm dialog
4. **Editor: Check Permissions** — Editors View → click own card → detail panel → review permissions and activity

---

## Key UX Decisions

### Role-based visibility
Admin-only surfaces (Hidden Groups, audit logs, session revocation) are clearly separated from editor-facing screens. Visual cues — warning banners, lock icons, muted colour on restricted items — reinforce what is and isn't accessible without requiring the user to read copy.

### Consistent 3-panel layout for the admin tool
Every admin screen uses the same skeleton: left sidebar navigation → centre list/content → right detail panel. This means users never lose their mental model when switching between Users, Editors, and Groups — only the centre and right panels change.

### Progressive disclosure in Group Creation
The 4-step wizard surfaces only what's needed at each stage. Basics first (name, visibility), then configuration, then membership, then permissions. This reduces cognitive load versus a single long form and makes it harder to accidentally misconfigure a sensitive group.

### Inherited permissions with override transparency
Group Inspection and User Inspection both show where permissions come from (role, parent group, direct override) rather than just the final value. A contextual info line ("inherited from Engineering, cannot be overridden here") prevents admin confusion when a toggle appears disabled.

### Destructive actions require confirmation
Suspending a user, revealing a hidden group, and revoking sessions all go through a confirmation step. Reveal and suspend use modal dialogs with explicit Yes/No choices; session revocation uses a labelled button that is visually separated from non-destructive actions.

### Dark theme for high-density tools, light for personal screens
Admin, browser, mobile, and test screens use dark backgrounds — appropriate for focus-heavy or ambient-light environments. Profile and Self-Reflection use light themes, matching the warmer, personal nature of those contexts.

### Colour as role signal
Each portfolio section has a consistent accent colour used across the site map, navigation flow, and cover card — indigo for admin/management, sky blue for browser, emerald for mobile, amber for testing, pink for profile, orange for journaling. This makes the portfolio itself navigable at a glance.
