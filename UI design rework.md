# Productivity99 — UI Polish & Rearrangement Plan

## Goal

Make the site feel more polished, focused, and Stripe-like:

- Put the main catchline and value proposition at the very top.
- Move **How it works** directly below the hero.
- Improve hierarchy, spacing, typography, buttons, cards, and section flow.
- Keep the existing content and functionality intact.
- Avoid a dark, busy, or overly decorated interface.

## Current order

1. Hero: “A classroom without borders”
2. Role cards: Teachers / Students / Study circles
3. How it works: “Five steps from sign-up to streak”
4. App preview: “Inside the app”
5. Features
6. Build details
7. FAQ
8. Final CTA

## Target order

1. **Hero / catchline**
2. **How it works**
3. **Role cards**
4. **Inside the app**
5. **Features**
6. **Build details**
7. **FAQ**
8. **Final CTA**

The catchline should appear before “How it works” so visitors immediately understand what Productivity99 does and why it matters.

---

## 1. Hero section

### Change

Move the hero to the absolute top of the page, directly after the header.

Use this structure:

```html
<section class="hero">
  <div class="hero-inner">
    <p class="hero-eyebrow">Study on your own clock</p>

    <h1 class="hero-title">
      A classroom without borders.
    </h1>

    <p class="hero-subtitle">
      Teach anywhere. Learn from everywhere. Set goals, track every study
      session, and trade ideas in a community that keeps you moving.
    </p>

    <div class="hero-actions">
      <a href="#signup" class="btn btn-primary">Open Prod99</a>
      <a href="#how-it-works" class="btn btn-secondary">See how it works</a>
    </div>

    <p class="hero-note">
      No email needed to get started.
    </p>
  </div>
</section>
```

### Copy update

Use this exact hero copy:

```text
Study on your own clock

A classroom without borders.

Teach anywhere. Learn from everywhere. Set goals, track every study
session, and trade ideas in a community that keeps you moving.

Open Prod99
See how it works

No email needed to get started.
```

### Design rules

- Use a white background.
- Center the hero content.
- Keep the hero concise: one eyebrow, one headline, one supporting paragraph, two buttons.
- Use `#0a2540` for the headline.
- Use `#425466` for the supporting paragraph.
- Use `#635bff` for the primary CTA.
- Add generous top and bottom padding: `96px` on mobile, `128px` on desktop.
- Do not add a large illustration or 3D object to the hero; the product preview should come later.

### CSS

```css
.hero {
  padding: 96px 24px;
  background: #ffffff;
  text-align: center;
}

.hero-inner {
  max-width: 820px;
  margin: 0 auto;
}

.hero-eyebrow {
  display: inline-block;
  margin-bottom: 16px;
  padding: 6px 12px;
  border: 1px solid #e6ebf1;
  border-radius: 999px;
  background: #f6f9fc;
  color: #635bff;
  font-size: 13px;
  font-weight: 600;
  letter-spacing: 0.02em;
}

.hero-title {
  margin: 0 0 20px;
  font-size: clamp(38px, 6vw, 64px);
  line-height: 1.05;
  letter-spacing: -0.03em;
  font-weight: 600;
  color: #0a2540;
}

.hero-subtitle {
  max-width: 640px;
  margin: 0 auto 32px;
  font-size: 18px;
  line-height: 1.6;
  color: #425466;
}

.hero-actions {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 12px;
}

.hero-note {
  margin-top: 16px;
  font-size: 14px;
  color: #6b7c93;
}
```

---

## 2. How it works

### Change

Move the entire **“Five steps from sign-up to streak”** section immediately after the hero.

Add this id to the section:

```html
<section id="how-it-works" class="how-it-works">
```

Update the “See how it works” button in the hero to link to:

```html
<a href="#how-it-works" class="btn btn-secondary">See how it works</a>
```

### Section structure

```html
<section id="how-it-works" class="how-it-works">
  <div class="section-inner">
    <p class="section-eyebrow">How it works</p>

    <h2 class="section-title">
      Five steps from sign-up to streak.
    </h2>

    <p class="section-subtitle">
      Everything happens in one workspace. Here is the path most people take.
    </p>

    <div class="steps-grid">
      <!-- Existing five steps -->
    </div>
  </div>
</section>
```

### Design rules

- Use a light background: `#f6f9fc`.
- Display the five steps in a responsive grid.
- Use 1 column on mobile, 2 columns on tablet, and 5 columns on wide desktop.
- Put the step number in a small circular badge.
- Keep each step short and scannable.
- Use a subtle border and very small shadow.

### CSS

```css
.how-it-works {
  padding: 96px 24px;
  background: #f6f9fc;
}

.steps-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 16px;
  margin-top: 48px;
}

@media (max-width: 1024px) {
  .steps-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 640px) {
  .steps-grid {
    grid-template-columns: 1fr;
  }
}

.step-card {
  padding: 24px;
  background: #ffffff;
  border: 1px solid #e6ebf1;
  border-radius: 12px;
  box-shadow: 0 1px 2px rgba(10, 37, 64, 0.06);
}

.step-number {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 32px;
  height: 32px;
  margin-bottom: 16px;
  border-radius: 999px;
  background: #f0edff;
  color: #533afd;
  font-weight: 700;
  font-size: 14px;
}

.step-title {
  margin: 0 0 8px;
  font-size: 17px;
  font-weight: 600;
  color: #0a2540;
}

.step-copy {
  margin: 0;
  font-size: 14px;
  line-height: 1.55;
  color: #425466;
}
```

---

## 3. Role cards

### Change

Move the Teachers / Students / Study circles cards below **How it works**.

Use this section order:

```text
Hero
How it works
Teachers / Students / Study circles
Inside the app
Features
```

### Design rules

- Keep the existing copy.
- Use three equal-width cards.
- Add a small icon or visual marker to each card.
- Use white cards on a white or very light background.
- Make the card titles stronger than the descriptions.
- Add hover elevation only if it does not distract from the page.

### CSS

```css
.roles-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  margin-top: 48px;
}

@media (max-width: 900px) {
  .roles-grid {
    grid-template-columns: 1fr;
  }
}

.role-card {
  padding: 28px;
  background: #ffffff;
  border: 1px solid #e6ebf1;
  border-radius: 12px;
}

.role-title {
  margin: 16px 0 8px;
  font-size: 18px;
  font-weight: 600;
  color: #0a2540;
}

.role-copy {
  margin: 0;
  font-size: 15px;
  line-height: 1.6;
  color: #425466;
}
```

---

## 4. Inside the app

### Change

Keep the app preview after the role cards.

Update the heading structure to:

```html
<p class="section-eyebrow">Inside the app</p>

<h2 class="section-title">
  A quick look at the three tools.
</h2>

<p class="section-subtitle">
  Goals, study sessions, and community updates—drawn from sample data.
</p>
```

### Design rules

- Place the app preview in a browser-style frame.
- Use a soft shadow and a 1px border.
- Keep the dashboard mock readable.
- Add a clear disclaimer below it:

```text
Sample data. Nothing here is connected to your account.
```

### CSS

```css
.app-preview {
  max-width: 1040px;
  margin: 48px auto 0;
  padding: 8px;
  background: #ffffff;
  border: 1px solid #e6ebf1;
  border-radius: 16px;
  box-shadow: 0 12px 40px rgba(10, 37, 64, 0.08);
  overflow: hidden;
}

.app-preview-bar {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 12px 16px;
  border-bottom: 1px solid #e6ebf1;
}

.app-preview-dot {
  width: 10px;
  height: 10px;
  border-radius: 999px;
  background: #e6ebf1;
}
```

---

## 5. Global UI polish

### Typography

Use a consistent type scale:

```css
body {
  font-family: "Inter", system-ui, -apple-system, BlinkMacSystemFont, sans-serif;
  color: #425466;
  line-height: 1.6;
}

h1,
h2,
h3 {
  color: #0a2540;
  letter-spacing: -0.02em;
}

h1 {
  font-size: clamp(38px, 6vw, 64px);
  font-weight: 600;
  line-height: 1.05;
}

h2 {
  font-size: clamp(28px, 4vw, 40px);
  font-weight: 600;
  line-height: 1.15;
}

h3 {
  font-size: 20px;
  font-weight: 600;
}

.section-eyebrow {
  margin-bottom: 12px;
  color: #635bff;
  font-size: 13px;
  font-weight: 700;
  letter-spacing: 0.04em;
  text-transform: uppercase;
}

.section-title {
  margin-bottom: 16px;
}

.section-subtitle {
  max-width: 620px;
  margin: 0 auto;
  color: #6b7c93;
}
```

### Buttons

```css
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  padding: 12px 20px;
  border-radius: 8px;
  font-size: 15px;
  font-weight: 600;
  text-decoration: none;
  transition: background 0.15s ease, border-color 0.15s ease,
    color 0.15s ease, transform 0.15s ease;
}

.btn-primary {
  background: #635bff;
  color: #ffffff;
  border: 1px solid #635bff;
}

.btn-primary:hover {
  background: #533afd;
  border-color: #533afd;
}

.btn-secondary {
  background: #ffffff;
  color: #635bff;
  border: 1px solid #e6ebf1;
}

.btn-secondary:hover {
  border-color: #635bff;
}

.btn:focus-visible {
  outline: 3px solid rgba(99, 91, 255, 0.35);
  outline-offset: 2px;
}
```

### Cards

```css
.card {
  background: #ffffff;
  border: 1px solid #e6ebf1;
  border-radius: 12px;
  padding: 24px;
  box-shadow: 0 1px 2px rgba(10, 37, 64, 0.06);
}

.card:hover {
  box-shadow: 0 6px 24px rgba(10, 37, 64, 0.08);
}
```

### Section spacing

```css
section {
  padding: 96px 24px;
}

.section-inner {
  max-width: 1120px;
  margin: 0 auto;
}

@media (max-width: 640px) {
  section {
    padding: 64px 20px;
  }
}
```

---

## 6. Header polish

### Change

Make the header simpler and more Stripe-like.

Use:

```text
Prod99 logo | Teachers | Students | Features | FAQ | Open Prod99
```

### Design rules

- Use a white, sticky header.
- Add a subtle bottom border: `1px solid #e6ebf1`.
- Keep the logo on the left.
- Keep navigation links centered or right-aligned.
- Keep only one primary CTA: **Open Prod99**.
- Reduce visual noise; remove duplicate or overly prominent controls.

### CSS

```css
.site-header {
  position: sticky;
  top: 0;
  z-index: 50;
  background: rgba(255, 255, 255, 0.92);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid #e6ebf1;
}

.header-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
  max-width: 1120px;
  margin: 0 auto;
  padding: 16px 24px;
}

.nav-link {
  color: #425466;
  font-size: 14px;
  font-weight: 500;
  text-decoration: none;
}

.nav-link:hover {
  color: #0a2540;
}
```

---

## 7. Content edits

### Hero

Replace the current opening headline area with:

```text
Study on your own clock

A classroom without borders.

Teach anywhere. Learn from everywhere. Set goals, track every study
session, and trade ideas in a community that keeps you moving.

Open Prod99
See how it works

No email needed to get started.
```

### How it works

Keep the existing heading:

```text
Five steps from sign-up to streak.
```

Keep the existing supporting line:

```text
Everything happens in one workspace. Here is the path most people take.
```

### Features

Keep the existing section heading:

```text
Everything a borderless classroom needs.
```

Use these three feature blocks:

```text
Session timer
Focus first, log automatically.
Start a session when you sit down, then stop it when you finish to record your study time.

Weekly progress
See your progress take shape.
Track your study time across the week with a chart that makes your habits easy to spot.

Goal tracker
Turn goals into steady progress.
Set a goal and update its progress as you work toward milestones you can share.
```

### Final CTA

Use:

```text
Ready to study on your own clock?

Create an account in under a minute and start your first session.

Open Prod99
```

---

## 8. Accessibility

- Ensure all buttons and links have visible focus states.
- Maintain at least 4.5:1 contrast for body text.
- Use semantic HTML: `header`, `main`, `section`, `h1`, `h2`, `nav`, and `footer`.
- Ensure the mobile menu is keyboard accessible.
- Add `aria-label` to icon-only buttons.
- Ensure the command palette can be closed with `Escape`.

---

## 9. Implementation checklist

- [ ] Move the hero to the top.
- [ ] Add the eyebrow: “Study on your own clock”.
- [ ] Update the hero headline and subtitle.
- [ ] Add two hero CTAs: “Open Prod99” and “See how it works”.
- [ ] Link “See how it works” to `#how-it-works`.
- [ ] Move “Five steps from sign-up to streak” directly below the hero.
- [ ] Move Teachers / Students / Study circles below How it works.
- [ ] Keep “Inside the app” after the role cards.
- [ ] Apply the new color, typography, button, and card system.
- [ ] Reduce shadows and visual noise.
- [ ] Improve mobile spacing and grid behavior.
- [ ] Test keyboard navigation and focus states.
- [ ] Test the page at 360px, 768px, 1024px, and 1440px widths.
