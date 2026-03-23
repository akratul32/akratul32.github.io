# Website Administrator Guide

A complete, beginner-friendly guide for editing every page and section on your academic website.

---

## 1. Project Structure Overview

| Folder | Purpose |
|--------|---------|
| `content/home/` | All homepage widget sections (About, Education, Skills, etc.) |
| `content/authors/admin/` | Your profile data (`_index.md`) and avatar image |
| `content/journal/` | Journal article publication entries |
| `content/conference/` | Conference proceeding publication entries |
| `content/poster/` | Poster publication entries |
| `content/project/` | Individual project entries |
| `content/event/` | Individual event entries |
| `content/post/` | News/blog posts |
| `static/` | Raw files (CV PDFs, images) served directly at your URL |
| `assets/scss/custom.scss` | All custom styling, colors, hover effects, and layout |
| `config/_default/menus.yaml` | Top navigation bar links and ordering |

---

## 2. How the Homepage Works

Your website is a **single-page scrolling layout**. All sections stack vertically on one page.

- **Section order** is controlled by `weight:` in each file's front matter. Lower weight = appears higher on the page.
- **Section visibility** is controlled by `active:`. Set to `false` to hide a section.

### Current Weight Map

| Weight | Section | File |
|--------|---------|------|
| 10 | About Me | `content/home/about.md` |
| 20 | Education | `content/home/education.md` |
| 25 | Certifications & Memberships | `content/home/certifications.md` |
| 30 | Journal Articles | `content/home/journals.md` |
| — | Conference Proceedings | `content/home/conferences.md` |
| — | Posters | `content/home/posters.md` |
| 40 | Projects | `content/home/projects.md` |
| 50 | Experience | `content/home/experience.md` |
| 54 | Leadership & Activities | `content/home/leadership.md` |
| 60 | Events | `content/home/events.md` |
| 65 | Technical Skills | `content/home/skills.md` |
| 70 | Contact | `content/home/contact.md` |

**To change section order:** Edit the `weight:` number. To swap two sections, swap their weights.

---

## 3. Editing Each Section — step by step

---

### 3.1 About Me

**Files involved:**
- `content/home/about.md` — section title and Download CV button
- `content/authors/admin/_index.md` — your bio text, interests, affiliations, social links

**To change your bio text:**
Open `content/authors/admin/_index.md` and edit the text under `bio:`.

**To change Research Interests:**
In the same file, edit the `interests:` list:
```yaml
interests:
  - AI for Construction
  - BIM Automation
  - Robotics
  - Your New Interest Here
```

**To change your profile picture:**
Replace the file at `content/authors/admin/avatar.jpg` (or `.jpeg/.png`) with your new photo. Keep the filename starting with `avatar`.

**To change the CV download button:**
Open `content/home/about.md` and update the `href` in the HTML:
```html
<a class="btn btn-primary" href="/assets/YOUR_NEW_CV.pdf" target="_blank">
  <i class="fas fa-download"></i> Download CV
</a>
```
(Make sure the PDF file exists in `static/assets/`.)

**To change your role, university, or social links:**
Edit the front matter in `content/authors/admin/_index.md`:
```yaml
role: Ph.D. Student / Graduate Research Assistant
organizations:
  - name: University of Texas at Arlington
    url: https://www.uta.edu
social:
  - icon: envelope
    icon_pack: fas
    link: 'mailto:your@email.edu'
  - icon: linkedin
    icon_pack: fab
    link: https://www.linkedin.com/in/your-profile/
```

---

### 3.2 Education

**File:** `content/home/education.md`

**To add a new degree**, add a new block under `experience:`:
```yaml
  - title: Master of Science in Civil Engineering
    company: University Name
    company_url: 'https://university.edu'
    location: City, State
    date_start: '2020-01-01'
    date_end: '2022-05-15'
    description: |2-
        GPA: 3.90/4.00
        Focus: Your area of focus.
```

**To remove a degree:** Delete the entire block (from `- title:` to the last line of `description`).

**Important rules:**
- Indentation matters! Use exactly 4 spaces for each level.
- `date_end: ''` (empty string) means "Present".
- `|2-` lets you write multi-line descriptions with bullet points using `*`.

---

### 3.3 Certifications & Memberships

**File:** `content/home/certifications.md`

This section uses **HTML card blocks**. Each card is wrapped in `<div class="cert-card">`.

**Current categories:** License, Memberships, AI/Data/ML Training, Project Management.

**To add a new certification entry** to an existing category, add a `<li>` inside the relevant `<ul>`:
```html
<div class="cert-card">
<h4>🤝 Memberships</h4>
<ul>
<li>Your existing membership</li>
<li>Your NEW Membership Entry (Year–Present)</li>
</ul>
</div>
```

**To add a new category**, copy-paste this template inside the `<div class="cert-grid">`:
```html
<div class="cert-card">
<h4>🏆 Your New Category</h4>
<ul>
<li>Item 1</li>
<li>Item 2</li>
</ul>
</div>
```

**To remove a category:** Delete the entire `<div class="cert-card">...</div>` block.

**To change the section title or subtitle:** Edit the `title:` and `subtitle:` in the YAML front matter at the top.

---

### 3.4 Journal Articles

**Widget file:** `content/home/journals.md` (controls how the section appears on the homepage)  
**Content entries:** `content/journal/` folder

**To add a new journal article:**
1. Create a new folder: `content/journal/my-new-paper/`
2. Create an `index.md` file inside it:
```yaml
---
title: "Your Paper Title"
authors:
  - admin
  - Co-Author Name
date: '2025-06-15'
publication_types: ['2']
publication: "Journal Name (Publisher)"
abstract: "Your paper abstract here."
url_pdf: "https://link-to-pdf.com"
doi: "10.1234/5678"
---
```

**To remove a paper:** Delete its folder from `content/journal/`.

---

### 3.5 Conference Proceedings

**Widget file:** `content/home/conferences.md`  
**Content entries:** `content/conference/` folder

Works identically to Journals above. Create a folder inside `content/conference/` with an `index.md`.

Use `publication_types: ['1']` for conference papers.

---

### 3.6 Posters

**Widget file:** `content/home/posters.md`  
**Content entries:** `content/poster/` folder

Same structure as Journals/Conferences. Create a folder inside `content/poster/` with an `index.md`.

---

### 3.7 Projects

**Widget file:** `content/home/projects.md`  
**Content entries:** `content/project/` folder

**To add a new project:**
1. Create a folder: `content/project/my-new-project/`
2. Add an `index.md`:
```yaml
---
title: "My New Project"
summary: "A brief description of the project."
tags:
  - AI
  - Construction
date: '2025-01-01'
external_link: ''
image:
  focal_point: Smart
---
Optional longer description here.
```
3. Drop an image named `featured.jpg` (or `.png`) into the same folder — this auto-appears as the project thumbnail.

**To remove:** Delete the project folder.

---

### 3.8 Experience

**File:** `content/home/experience.md`

This uses the `experience` widget with a timeline layout. Each role is a block under `experience:`.

**To add a new role:**
```yaml
  - title: "[Tag] Your Role Title"
    company: Company or University Name
    company_url: 'https://company.com'
    location: City, State
    date_start: '2023-01-01'
    date_end: ''
    description: |2-
        * Responsibility or achievement bullet point 1.
        * Responsibility or achievement bullet point 2.
```

**Tags used:** `[Research]`, `[Teaching]`, `[Industry]` — these appear in the title for visual categorization.

**To remove a role:** Delete its entire block.

---

### 3.9 Leadership & Activities

**File:** `content/home/leadership.md`

Works exactly the same as Experience above. Each entry is a block under `experience:`.

**To add a new activity:**
```yaml
  - title: "[Outreach] Activity Title"
    company: Organization Name
    date_start: '2024-01-01'
    date_end: ''
    description: |2-
        * Description of what you did.
```

---

### 3.10 Events

**Widget file:** `content/home/events.md`  
**Content entries:** `content/event/` folder

**To add a new event:**
1. Create a folder: `content/event/my-hackathon/`
2. Add `index.md` with front matter (title, date, summary, tags).
3. Add `featured.jpg` for the event image.

---

### 3.11 Technical Skills

**File:** `content/home/skills.md`

This section uses **HTML card blocks**. Each skill category is a `<div class="skill-card">`.

**To add a new skill** to an existing category, edit the `<p>` text:
```html
<div class="skill-card">
<h4>💻 Programming</h4>
<p>Python &nbsp;|&nbsp; C++ &nbsp;|&nbsp; C# &nbsp;|&nbsp; Your New Skill</p>
</div>
```

**To add a new skill category:**
```html
<div class="skill-card">
<h4>🔬 Your Category Name</h4>
<p>Skill 1 &nbsp;|&nbsp; Skill 2 &nbsp;|&nbsp; Skill 3</p>
</div>
```

⚠️ Use `&nbsp;|&nbsp;` (not just `|`) as the separator to get proper spacing.

**To remove a category:** Delete the entire `<div class="skill-card">...</div>` block.

---

### 3.12 Contact

**File:** `content/home/contact.md`

Open it and edit:
```yaml
email: your@email.edu
address:
  street: "Your Building"
  city: "City"
  region: "State"
  postcode: "ZIP"
```

---

### 3.13 Recent News

**Widget file:** `content/home/news.md`  
**Content entries:** `content/post/` folder

**To add a news post:**
1. Create a folder: `content/post/my-news/`
2. Add `index.md`:
```yaml
---
title: "Your News Title"
date: 2025-06-01
summary: "Brief summary that appears on the homepage."
---
Full text here.
```

---

## 4. Navigation Menu

**File:** `config/_default/menus.yaml`

Each menu item looks like:
```yaml
  - name: Education
    url: /#education
    weight: 20
```

- `name:` = text shown in the navbar
- `url:` = must start with `/#` followed by the section ID (matches the filename without `.md`)
- `weight:` = order in the navbar (lower = more to the left)

**To add a menu item:**
```yaml
  - name: New Section
    url: /#new-section
    weight: 55
```

**To remove:** Delete the 3-line block.

---

## 5. Styling (Colors, Hover, Layout)

**File:** `assets/scss/custom.scss`

| What | Where in the file |
|------|--------------------|
| Color palette | `:root { }` block at top — edit CSS variables like `--primary`, `--accent` |
| Hover effect | `@mixin hover-card { }` — controls lift, shadow, border |
| Heading sizes | `h1 { }`, `h2 { }`, etc. — uses `clamp()` for responsive sizing |
| Section backgrounds | `section:nth-child(even/odd)` — alternating gradient |
| Navbar | `.navbar { }` — frosted glass properties |
| Cert card accent bar | `.cert-card::before` — the blue left border |
| Skill card underline | `.skill-card::after` — the expanding bottom accent |

### Quick color changes:
```scss
:root {
  --primary: #0F1E3D;    // Main heading color (navy)
  --secondary: #1A5276;  // Subheading color (teal-blue)
  --accent: #2E86C1;     // Links, buttons, highlights (sky blue)
  --text-body: #2C3E50;  // Body text color
  --bg-page: #F0F4F8;    // Page background
}
```

---

## 6. Common Tasks

### "How do I update my CV?"
1. Put your new PDF in `static/assets/` with the same filename.
2. If the filename changed, update `href` in `content/home/about.md`.

### "How do I add a new project?"
1. Duplicate an existing folder in `content/project/`.
2. Edit `index.md` and replace `featured.jpg`.

### "How do I reorder sections?"
Change the `weight:` value in the front matter of each file in `content/home/`. Lower = higher on page.

### "How do I hide a section?"
Add `active: false` in the front matter of the widget file.

### "How do I change the website title?"
Edit `config/_default/params.yaml` — look for `title:`.

---

## 7. Running the Website

**Preview locally:**
```bash
hugo server -p 1313
```
Then open http://localhost:1313 in your browser.

**Build for deployment:**
```bash
hugo
```
Upload the `public/` folder to GitHub Pages, Netlify, or any web host.

---

## 8. Troubleshooting

| Problem | Solution |
|---------|----------|
| Site didn't update | Kill Hugo (`Ctrl+C`) and restart it |
| Menu link goes to 404 | Make sure `url:` in `menus.yaml` starts with `/#` |
| Image not showing | Image must be named `featured.jpg` and inside the item's folder |
| Section not appearing | Check `active: true` and correct `weight:` in front matter |
| YAML error / site won't build | Check indentation — YAML requires consistent spaces, not tabs |
| HTML not rendering | Make sure `design: columns: "1"` is set for `blank` widgets with HTML content |
