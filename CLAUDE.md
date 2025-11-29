# CLAUDE.md - Repository Guide for AI Assistants

**Repository:** Kovacevix/Kovacevix
**Last Updated:** 2025-11-29
**Project Type:** Frontend Web Application (Tokyo Travel Planner)
**Primary Language:** HTML5, CSS3, JavaScript (Portuguese interface)

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Current Repository State](#current-repository-state)
3. [Codebase Structure](#codebase-structure)
4. [Technology Stack](#technology-stack)
5. [Development Workflows](#development-workflows)
6. [Key Conventions](#key-conventions)
7. [Data Persistence](#data-persistence)
8. [Git History & Recovery](#git-history--recovery)
9. [Working with This Repository](#working-with-this-repository)

---

## Project Overview

This is a **personal travel planning and diary web application** specifically designed for planning trips to Tokyo, Japan. The application provides:

- **Trip Planning**: Create and organize activities by day and time
- **Travel Diary**: Log experiences with optional photo links
- **Information Hub**: Travel tips, useful Japanese phrases, and practical information
- **Responsive Design**: Mobile-friendly interface using Bootstrap

**Target Audience**: Portuguese-speaking travelers to Tokyo
**Architecture**: Single-page application (SPA) with client-side routing
**Data Storage**: Browser localStorage (no backend server)

---

## Current Repository State

### Status: Minimal State (Post-Cleanup)

As of the most recent commits (2025-11-29), all HTML application files have been deleted:

```
Recent Deletions:
- verplanos.html (plan viewing)
- navbar.html (navigation component)
- intro.html (welcome page)
- informacoes uteis.html (travel information)
- index.html (login/entry page)
- criarPlanos.html (plan creation)
- diario.html (travel diary)
- dicas.html (travel tips)
- frases.html (Japanese phrases)
```

**Current Files:**
```
/home/user/Kovacevix/
├── .git/           # Full git history (50 commits)
└── README.md       # GitHub profile readme
```

**Important**: The complete project history is preserved in git. All deleted files can be recovered from earlier commits.

---

## Codebase Structure

### Original Application Structure (Pre-Deletion)

```
Kovacevix/
├── index.html                  # Entry point / Login page
├── intro.html                  # Welcome/introduction page
├── navbar.html                 # Reusable navigation component
├── criarPlanos.html           # Plan creation interface
├── verplanos.html             # Plan viewing/management
├── diario.html                # Travel diary with photos
├── dicas.html                 # Travel tips and recommendations
├── frases.html                # Useful Japanese phrases
├── informacoes uteis.html     # Practical travel information
└── README.md                   # Documentation
```

### Page Relationships

```
index.html (Login)
    ↓
intro.html (Welcome)
    ↓
├── criarPlanos.html → verplanos.html
├── diario.html
├── dicas.html
├── frases.html
└── informacoes uteis.html
```

All pages load `navbar.html` dynamically via Fetch API for consistent navigation.

---

## Technology Stack

### Frontend Technologies

**Core:**
- **HTML5**: Semantic markup with Portuguese content
- **CSS3**: Modern styling with animations and responsive design
- **JavaScript (Vanilla)**: Client-side logic, no framework

**UI Framework:**
- **Bootstrap 4.5.2**: CSS framework for responsive layout
- **jQuery 3.5.1**: DOM manipulation helper
- **Popper.js 2.5.3**: Tooltip and popover positioning

**External Services:**
- **Google Fonts**: Poppins, Roboto, Orbitron typefaces
- **Unsplash API**: Dynamic background images

### Key Features

1. **No Build Process**: Static HTML files, no webpack/babel/etc.
2. **No Backend**: Pure client-side application
3. **No Package Manager**: Dependencies loaded via CDN
4. **localStorage API**: All data persisted in browser
5. **Responsive Design**: Mobile-first with media queries
6. **Dynamic Component Loading**: Fetch API for navbar injection

---

## Development Workflows

### Standard Development Flow

Since this is a static site with no build process:

1. **Direct File Editing**: Edit HTML/CSS/JS files directly
2. **Browser Testing**: Open files in browser (file:// protocol or local server)
3. **Git Commits**: Standard git workflow for version control
4. **Deployment**: Copy files to static hosting (GitHub Pages compatible)

### Local Development

**Option 1: File Protocol**
```bash
# Open directly in browser
open index.html  # macOS
xdg-open index.html  # Linux
start index.html  # Windows
```

**Option 2: Local Server** (Recommended for Fetch API)
```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000

# Node.js (with http-server)
npx http-server -p 8000
```

Then navigate to: `http://localhost:8000/index.html`

### Testing localStorage

Since the app uses localStorage:
- Use browser DevTools → Application → Local Storage
- Data persists between sessions
- Clear storage to reset: `localStorage.clear()`

---

## Key Conventions

### Code Style

**HTML:**
- Portuguese language attribute: `<html lang="pt">`
- Semantic HTML5 elements preferred
- Inline styles common (no separate CSS files)
- Bootstrap classes for layout

**CSS:**
- Inline `<style>` tags within HTML files
- Flexbox and Grid for layouts
- Media queries for responsive breakpoints
- CSS variables occasionally used

**JavaScript:**
- Vanilla JavaScript (ES5/ES6 mix)
- Event listeners attached in `<script>` tags
- localStorage for persistence
- Fetch API for loading components

### Naming Conventions

**Files:**
- Lowercase with spaces: `informacoes uteis.html`
- Portuguese descriptive names
- `.html` extension for all pages

**localStorage Keys:**
- `journalEntries`: Array of diary entries
- `plans`: Array of trip plans

**CSS Classes:**
- Bootstrap convention: `container`, `row`, `col-*`
- Custom classes: descriptive Portuguese names

### Component Pattern

**navbar.html Loading Pattern:**
```javascript
fetch('navbar.html')
    .then(response => response.text())
    .then(data => {
        document.getElementById('navbar-container').innerHTML = data;
    });
```

Used consistently across pages for navigation bar injection.

---

## Data Persistence

### localStorage Schema

**Journal Entries:**
```javascript
{
  journalDay: "2024-09-15",
  journalNote: "Visited Senso-ji Temple...",
  photoUrl: "https://example.com/photo.jpg"
}
```

**Plans:**
```javascript
{
  day: "Day 1",
  time: "09:00",
  activity: "Visit Tsukiji Market"
}
```

### Data Operations

**Saving:**
```javascript
localStorage.setItem('journalEntries', JSON.stringify(entries));
```

**Loading:**
```javascript
const entries = JSON.parse(localStorage.getItem('journalEntries')) || [];
```

**Important**: All data is client-side only. No server synchronization.

---

## Git History & Recovery

### Commit History

- **Total Commits**: 50
- **Date Range**: 2024-09-15 (initial commit) to 2025-11-29
- **Primary Contributor**: Kovacevix
- **Development Timeline**: Single-day intensive development (Sept 15, 2024)

### File Recovery

To recover deleted files from git history:

```bash
# View file at specific commit
git show <commit-hash>:index.html

# Restore specific file from commit
git checkout <commit-hash> -- index.html

# Restore all files from last working state
git checkout 43a6cad -- .  # Before deletions started

# Create new branch from earlier state
git checkout -b restore-point 43a6cad
```

### Important Commits

```
43a6cad - Last commit before deletions (Delete index.html)
0135435 - Delete informacoes uteis.html
51e8495 - Delete intro.html
9ed1042 - Delete navbar.html
8a4d9cd - Delete verplanos.html (most recent)
```

To restore to working application state, checkout before commit `8a4d9cd`.

---

## Working with This Repository

### For Code Modifications

1. **Restore Files First** (if needed):
   ```bash
   git checkout 43a6cad -- .
   ```

2. **Make Changes**: Edit HTML/CSS/JS as needed

3. **Test Locally**: Use local server for testing

4. **Commit Changes**:
   ```bash
   git add .
   git commit -m "Description of changes"
   ```

5. **Push to Branch**:
   ```bash
   git push -u origin claude/claude-md-mikwyee6jrn7avxa-01Np3aeZNPLoyzG2cMEY5FsH
   ```

### For Adding New Features

**Common Additions:**
- New destination pages (copy existing page structure)
- Additional localStorage data types
- New information sections
- Enhanced styling/animations

**Pattern to Follow:**
1. Create new `.html` file
2. Include Bootstrap CDN links
3. Add navbar loading script
4. Implement localStorage logic if needed
5. Update navigation links in `navbar.html`

### For Refactoring

**Potential Improvements:**
- Extract inline CSS to separate files
- Modularize JavaScript code
- Add build process (webpack/parcel)
- Implement proper routing (SPA framework)
- Add backend for data persistence
- Implement testing framework
- Add ESLint/Prettier for code quality

### For Bug Fixes

**Common Issues:**
- CORS errors: Use local server, not file:// protocol
- localStorage not persisting: Check browser settings
- Navigation not loading: Verify fetch() paths
- Bootstrap not styling: Check CDN links

### For Documentation

**Update This File When:**
- New pages are added
- Technology stack changes
- Data schema is modified
- New conventions are established
- Deployment process changes

---

## Additional Notes

### No Testing Framework

This repository has no automated tests. Testing is manual:
- Open pages in browser
- Test localStorage operations in DevTools
- Verify responsive design at different breakpoints
- Check cross-browser compatibility

### No CI/CD Pipeline

No automated deployment or continuous integration:
- Manual testing required
- Manual deployment to hosting
- No automated checks on pull requests

### Portuguese Language

All user-facing content is in Portuguese:
- UI text and labels
- Comments may be minimal
- Consider translation if internationalizing

### Static Hosting Compatible

This application can be hosted on:
- GitHub Pages
- Netlify
- Vercel
- Any static file server
- Amazon S3 + CloudFront
- Firebase Hosting

No server-side rendering or backend required.

---

## Quick Reference

### Restore Full Application
```bash
git checkout 43a6cad -- .
git checkout HEAD -- README.md  # Keep current README
```

### View Deleted File Content
```bash
git show HEAD~5:index.html
```

### Start Local Development
```bash
python -m http.server 8000
# Navigate to http://localhost:8000/index.html
```

### Clear Application Data
```javascript
// In browser console
localStorage.clear();
location.reload();
```

---

**For Questions or Issues:**
- Review git history for context
- Check localStorage in browser DevTools
- Verify CDN links are accessible
- Ensure local server is running (not file:// protocol)

**Repository Maintainer:** Kovacevix
**Contact:** 125938041+Kovacevic@users.noreply.github.com
