# Club Records Page Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build `club-records.html`, a self-contained HTML snippet for the NSUC TidyHQ site showing the all-time heaviest fish per species from club competition history.

**Architecture:** Single HTML file with embedded `<style>` block and a root `<div class="nsuc-records">`. No build tools — plain HTML/CSS following the patterns in `about.html` and `trophy-fish-2026.html`. Cards use CSS grid; fish photos are inline SVG silhouette placeholders styled in greyscale.

**Tech Stack:** HTML5, CSS3 (grid layout), inline SVG placeholders.

---

### Task 1: Create page skeleton

**Files:**
- Create: `club-records.html`

- [ ] **Step 1: Create the file with hero and section headers**

Create `club-records.html` at the repo root:

```html
<style>
  .nsuc-records {
    font-family: Georgia, 'Times New Roman', serif;
    font-size: 1.5rem;
    color: #1a1a1a;
    max-width: 860px;
    margin: 0 auto;
    line-height: 1.7;
  }

  .nsuc-records h2 {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 1.5rem;
    font-weight: 700;
    color: #00558b;
    border-bottom: 2px solid #00558b;
    padding-bottom: 0.3rem;
    margin-top: 2.5rem;
    margin-bottom: 1rem;
    text-transform: uppercase;
    letter-spacing: 0.04em;
  }

  .nsuc-records-hero {
    background: linear-gradient(135deg, #003f6b 0%, #00558b 60%, #0077b6 100%);
    color: #fff;
    border-radius: 6px;
    padding: 2.5rem 2rem;
    margin-bottom: 2rem;
    text-align: center;
  }

  .nsuc-records-hero h1 {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 2rem;
    font-weight: 900;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    margin: 0 0 0.5rem;
  }

  .nsuc-records-hero .tagline {
    font-size: 1rem;
    opacity: 0.85;
    font-style: italic;
    margin: 0;
  }
</style>

<div class="nsuc-records">

  <div class="nsuc-records-hero">
    <h1>Club Records</h1>
    <p class="tagline">All-time records &mdash; North Shore Underwater Club</p>
  </div>

  <h2>Premier Species</h2>
  <!-- premier cards go here -->

  <h2>Regular Species</h2>
  <!-- regular cards go here -->

</div>
```

- [ ] **Step 2: Open in browser to verify**

```bash
open club-records.html
```

Expected: Blue gradient hero with "CLUB RECORDS" title and italic tagline. Two blue uppercase section headers below.

- [ ] **Step 3: Commit**

```bash
git add club-records.html
git commit -m "feat: add club-records page skeleton"
```

---

### Task 2: Add card grid CSS and test card

**Files:**
- Modify: `club-records.html`

- [ ] **Step 1: Add card CSS to the `<style>` block**

Inside the `<style>` block, after `.nsuc-records-hero .tagline { ... }`, add:

```css
  .nsuc-records-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1rem;
    margin: 1rem 0 2rem;
  }

  .nsuc-record-card {
    background: #f0f7fc;
    border-left: 4px solid #00558b;
    border-radius: 6px;
    padding: 1rem;
    text-align: center;
  }

  .nsuc-record-photo {
    width: 100%;
    height: 130px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #dde9f3;
    border-radius: 4px;
    margin-bottom: 0.75rem;
    overflow: hidden;
  }

  .nsuc-record-photo svg {
    width: 85%;
    height: 85%;
  }

  .nsuc-record-species {
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 700;
    color: #00558b;
    font-size: 0.95rem;
    text-transform: uppercase;
    letter-spacing: 0.03em;
    margin-bottom: 0.4rem;
  }

  .nsuc-record-weight {
    font-family: Georgia, 'Times New Roman', serif;
    font-size: 1.4rem;
    font-weight: 700;
    color: #1a1a1a;
    margin-bottom: 0.2rem;
  }

  .nsuc-record-member {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 0.85rem;
    color: #555;
  }

  .nsuc-record-vacant .nsuc-record-weight,
  .nsuc-record-vacant .nsuc-record-member {
    color: #aaa;
    font-style: italic;
    font-size: 0.95rem;
    font-weight: normal;
  }

  @media (max-width: 600px) {
    .nsuc-records-grid {
      grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
    }
  }
```

- [ ] **Step 2: Replace the Premier Species placeholder with a single test card**

Replace `<!-- premier cards go here -->` with:

```html
  <div class="nsuc-records-grid">
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Kingfish</div>
      <div class="nsuc-record-weight">35.00 kg</div>
      <div class="nsuc-record-member">P. Sheppard</div>
    </div>
  </div>
```

- [ ] **Step 3: Open in browser to verify**

```bash
open club-records.html
```

Expected: One card under Premier Species — grey-blue fish silhouette in a light blue box, "KINGFISH" in blue caps, "35.00 kg" in large serif, "P. Sheppard" in small grey text below.

- [ ] **Step 4: Commit**

```bash
git add club-records.html
git commit -m "feat: add record card CSS and SVG silhouette placeholder"
```

---

### Task 3: Add all Premier Species cards

**Files:**
- Modify: `club-records.html`

The SVG silhouette is the same for every card. Reuse it verbatim — each card is identical except for species, weight, and member.

- [ ] **Step 1: Replace the entire Premier grid with all 6 species**

Replace the entire `<div class="nsuc-records-grid">…</div>` block under Premier Species (the one containing the single Kingfish test card from Task 2) with:

```html
  <div class="nsuc-records-grid">
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Kingfish</div>
      <div class="nsuc-record-weight">35.00 kg</div>
      <div class="nsuc-record-member">P. Sheppard</div>
    </div>
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Mulloway</div>
      <div class="nsuc-record-weight">34.40 kg</div>
      <div class="nsuc-record-member">A. Moderer</div>
    </div>
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Cobia</div>
      <div class="nsuc-record-weight">29.95 kg</div>
      <div class="nsuc-record-member">A. Price</div>
    </div>
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Spanish Mackerel</div>
      <div class="nsuc-record-weight">26.20 kg</div>
      <div class="nsuc-record-member">N. Blyth</div>
    </div>
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Dolphin Fish</div>
      <div class="nsuc-record-weight">8.80 kg</div>
      <div class="nsuc-record-member">J. Williams</div>
    </div>
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Snapper</div>
      <div class="nsuc-record-weight">7.30 kg</div>
      <div class="nsuc-record-member">J. Howard</div>
    </div>
  </div>
```

- [ ] **Step 2: Open in browser to verify**

```bash
open club-records.html
```

Expected: 6 Premier Species cards in a grid (3–4 per row on a wide browser), each with a fish silhouette and the correct species/weight/member data.

- [ ] **Step 3: Commit**

```bash
git add club-records.html
git commit -m "feat: add premier species records cards"
```

---

### Task 4: Add all Regular Species cards

**Files:**
- Modify: `club-records.html`

Vacant cards (Sand Whiting, Silver Trevally, Yellow Spot Sawtail) use the `nsuc-record-vacant` modifier class, which the CSS from Task 2 already styles as grey italic.

- [ ] **Step 1: Replace the Regular Species placeholder with all 12 cards**

Replace `<!-- regular cards go here -->` with:

```html
  <div class="nsuc-records-grid">
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Bonito</div>
      <div class="nsuc-record-weight">5.24 kg</div>
      <div class="nsuc-record-member">A. Scott</div>
    </div>
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Rock Blackfish</div>
      <div class="nsuc-record-weight">5.15 kg</div>
      <div class="nsuc-record-member">D. Fitzgerald</div>
    </div>
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Salmon</div>
      <div class="nsuc-record-weight">4.16 kg</div>
      <div class="nsuc-record-member">G. Kroie</div>
    </div>
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Blue Morwong</div>
      <div class="nsuc-record-weight">3.42 kg</div>
      <div class="nsuc-record-member">C. Maloney</div>
    </div>
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Red Morwong</div>
      <div class="nsuc-record-weight">2.335 kg</div>
      <div class="nsuc-record-member">M. Walsh</div>
    </div>
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Red Rock Cod</div>
      <div class="nsuc-record-weight">2.172 kg</div>
      <div class="nsuc-record-member">A. Price</div>
    </div>
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Luderick</div>
      <div class="nsuc-record-weight">1.938 kg</div>
      <div class="nsuc-record-member">A. Price</div>
    </div>
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Bream</div>
      <div class="nsuc-record-weight">1.690 kg</div>
      <div class="nsuc-record-member">M. Bonnici</div>
    </div>
    <div class="nsuc-record-card">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Goatfish</div>
      <div class="nsuc-record-weight">1.655 kg</div>
      <div class="nsuc-record-member">J. Chan</div>
    </div>
    <div class="nsuc-record-card nsuc-record-vacant">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Sand Whiting</div>
      <div class="nsuc-record-weight">Vacant</div>
      <div class="nsuc-record-member">&mdash;</div>
    </div>
    <div class="nsuc-record-card nsuc-record-vacant">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Silver Trevally</div>
      <div class="nsuc-record-weight">Vacant</div>
      <div class="nsuc-record-member">&mdash;</div>
    </div>
    <div class="nsuc-record-card nsuc-record-vacant">
      <div class="nsuc-record-photo">
        <svg viewBox="0 0 240 110" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <polygon points="28,55 0,28 0,82" fill="#8a9fb5"/>
          <ellipse cx="118" cy="55" rx="94" ry="40" fill="#6e8fa8"/>
          <polygon points="78,15 118,0 158,15" fill="#8a9fb5"/>
          <polygon points="100,72 122,92 152,76" fill="#8a9fb5"/>
          <circle cx="182" cy="48" r="11" fill="#cddbe8"/>
          <circle cx="185" cy="48" r="5" fill="#4a6a82"/>
        </svg>
      </div>
      <div class="nsuc-record-species">Yellow Spot Sawtail</div>
      <div class="nsuc-record-weight">Vacant</div>
      <div class="nsuc-record-member">&mdash;</div>
    </div>
  </div>
```

- [ ] **Step 2: Open in browser to verify**

```bash
open club-records.html
```

Expected: 12 Regular Species cards in a grid. Last 3 cards (Sand Whiting, Silver Trevally, Yellow Spot Sawtail) show "Vacant" in grey italic weight and an em dash for the member name. The other 9 show normal dark weight and grey member name.

- [ ] **Step 3: Commit**

```bash
git add club-records.html
git commit -m "feat: add regular species records cards"
```

---

### Task 5: Add note callout and final polish

**Files:**
- Modify: `club-records.html`

- [ ] **Step 1: Add note CSS to the `<style>` block**

After the `@media (max-width: 600px)` block, add:

```css
  .nsuc-records-note {
    background: #f0f7fc;
    border-left: 4px solid #00558b;
    border-radius: 4px;
    padding: 0.9rem 1.1rem;
    margin: 0.5rem 0 2rem;
    font-family: Arial, Helvetica, sans-serif;
    font-size: 0.9rem;
    color: #444;
  }

  .nsuc-records-note p {
    margin: 0;
  }
```

- [ ] **Step 2: Add note callout before the closing `</div>`**

Before the final `</div>` (closing `.nsuc-records`), add:

```html
  <div class="nsuc-records-note">
    <p>Records are all-time bests from NSUC club competition history. Sand Whiting, Silver Trevally and Yellow Spot Sawtail are newly established categories with no prior history.</p>
  </div>
```

- [ ] **Step 3: Full visual check in browser**

```bash
open club-records.html
```

Check all of the following:
- Hero banner: gradient, title, italic tagline
- Premier Species: 6 cards, correct species/weight/member for each
- Regular Species: 12 cards; first 9 have dark weight + grey member; last 3 show "Vacant" in grey italic
- Note callout below Regular grid: blue left border, grey text
- Resize to ~375px wide: cards reflow to 2 columns, no horizontal overflow

- [ ] **Step 4: Commit**

```bash
git add club-records.html
git commit -m "feat: complete club records page with note callout"
```
