# Simple Weight & Waist Tracker - Build Instructions

---

## Overview

Build a **beautiful, responsive weight and waist tracking web app** with essential features only. Focus on elegant design and smooth user experience.

---

## Data Format (MUST FOLLOW EXACTLY)

The app must work with this exact JSON structure:

```json
{
  "version": 1,
  "entries": [
    {
      "date": "2025-08-18",
      "weight": 80.1,
      "waist": 111
    }
  ]
}
```

**Data file:** [ww-tracker-data.json](ww-tracker-data.json)
- Contains 31 real entries from Aug 2025 to Feb 2026
- Weight: 80.1 kg → 72.0 kg (-8.1 kg)
- Waist: 111 cm → 100 cm (-11 cm)

---

## Core Features (Essential Only)

### 1. Progress Dashboard
- **Large progress cards** showing:
  - Current weight and waist
  - Total change (delta from first to last entry)
  - Direction arrows (↓ green for loss, ↑ red for gain, → gray for stable)
- **Beautiful SVG line chart:**
  - Dual series (weight in teal, waist in indigo)
  - Toggle visibility of each metric
  - Smooth curves (not straight lines)
  - Responsive and mobile-friendly

### 2. Add/Edit Entries
- Simple form with 3 fields:
  - Date (defaults to today)
  - Weight (kg)
  - Waist (cm)
- Save button adds new entry or updates existing (if date already exists)
- Clear form button

### 3. Entry List
- Show all entries in reverse chronological order
- Display: Date | Weight | Waist
- Edit and Delete buttons for each entry
- Delete requires confirmation

### 4. Import/Export
- **Export:** Download `ww-tracker-data.json` with all data
- **Import:** Upload JSON file to restore data
- Both buttons should be easily accessible

---

## Design Requirements (CRITICAL)

### Visual Design
- **Modern, clean, beautiful interface**
- **Mobile-first responsive design** (320px → 1440px)
- **Professional color palette:**
  - Primary: Modern teal/blue gradient
  - Success: Emerald green
  - Warning/Loss: Rose/red
  - Background: Soft gray/white (light mode), dark gray (dark mode)
- **Smooth rounded cards** (16-20px radius)
- **Subtle shadows** for depth
- **Beautiful SVG icons** throughout (use Heroicons or similar):
  - Scale icon for weight
  - Tape measure for waist
  - Calendar, plus, edit, delete, export, import icons

### Typography
- Import a modern font (e.g., Inter, DM Sans)
- Clear hierarchy: large numbers for metrics, smaller labels
- Good spacing and readability

### Dark Mode
- Full dark theme support
- Manual toggle (sun/moon icon) + respect system preference
- Smooth theme transition animation

### Animations (Essential)
- **Chart drawing:** Lines animate from left to right when rendered
- **Number counters:** Animate when values change
- **Button press:** Subtle scale effect on click
- **Card entry:** Fade-in on page load
- **Smooth transitions** between all states

---

## Technical Requirements

### Storage
- Use `localStorage` with key: `ww-tracker`
- Store data in exact format specified above

### Chart
- Custom SVG chart (no heavy libraries)
- Smooth bezier curves for lines
- Grid lines and axis labels
- 5 Y-axis ticks, up to 6 X-axis date labels
- Responsive viewBox
- Toggle buttons to show/hide each metric

### Responsive Breakpoints
- Mobile: 320-767px (single column, stacked layout)
- Tablet: 768-1023px (grid layout)
- Desktop: 1024px+ (wider grid with sidebar potential)

### File Structure
```
index.html          -- Single file is fine for simplicity
  OR
src/
  index.html        -- Shell
  css/
    styles.css      -- All styles
  js/
    app.js          -- Main logic
    chart.js        -- SVG chart rendering
```

---

## UI Layout

### Desktop Layout
```
┌─────────────────────────────────────────────┐
│  Header: "Weight & Waist Tracker"          │
│  [Theme Toggle] [Import] [Export]          │
├─────────────────────────────────────────────┤
│                                             │
│  ┌─────────────┐  ┌─────────────┐         │
│  │  Weight     │  │  Waist      │         │
│  │  72.0 kg    │  │  100 cm     │         │
│  │  ↓ -8.1 kg  │  │  ↓ -11 cm   │         │
│  └─────────────┘  └─────────────┘         │
│                                             │
│  ┌─────────────────────────────────────┐  │
│  │                                     │  │
│  │         BEAUTIFUL CHART             │  │
│  │                                     │  │
│  └─────────────────────────────────────┘  │
│                                             │
│  [Show Weight ✓] [Show Waist ✓]           │
│                                             │
│  ┌─────────────────────────────────────┐  │
│  │  Add Entry Form                     │  │
│  │  Date: [____] Weight: [____]        │  │
│  │  Waist: [____]  [Save] [Clear]      │  │
│  └─────────────────────────────────────┘  │
│                                             │
│  ┌─────────────────────────────────────┐  │
│  │  Entry List                         │  │
│  │  2026-02-09  72.0 kg  100 cm  [✏️ 🗑️] │
│  │  2026-02-02  72.8 kg  100 cm  [✏️ 🗑️] │
│  │  ...                                │  │
│  └─────────────────────────────────────┘  │
└─────────────────────────────────────────────┘
```

### Mobile Layout
- Stack all cards vertically
- Full-width chart
- Form fields stack vertically
- Entry list becomes card-style with larger touch targets

---

## Quality Standards

### Must Look Professional
- Every element should be polished
- Consistent spacing (use 4px/8px/16px/24px grid)
- Proper alignment and visual hierarchy
- Beautiful empty states (e.g., "No entries yet" with icon)

### Must Be Smooth
- All animations should be 60fps
- No janky interactions
- Fast load time (< 1 second)

### Must Be Accessible
- Proper ARIA labels on interactive elements
- Keyboard navigation support
- High contrast colors
- Touch targets minimum 44x44px

---

## Implementation Priority

1. **Data layer** - localStorage CRUD, import/export
2. **Design system** - Colors, typography, spacing
3. **Progress cards** - Current stats with deltas
4. **Chart rendering** - Beautiful SVG chart with animations
5. **Entry form** - Add/edit functionality
6. **Entry list** - Display with edit/delete
7. **Dark mode** - Theme toggle
8. **Polish** - Animations, transitions, micro-interactions

---

## Color Palette Example

```css
/* Light Mode */
--primary: #0891b2;      /* Cyan 600 */
--primary-light: #06b6d4; /* Cyan 500 */
--success: #10b981;      /* Emerald 500 */
--danger: #f43f5e;       /* Rose 500 */
--bg: #f9fafb;           /* Gray 50 */
--card: #ffffff;
--text: #111827;         /* Gray 900 */
--text-secondary: #6b7280; /* Gray 500 */

/* Dark Mode */
--bg-dark: #111827;      /* Gray 900 */
--card-dark: #1f2937;    /* Gray 800 */
--text-dark: #f9fafb;    /* Gray 50 */
```

---

## What NOT to Include

- No BMI calculator
- No goal setting
- No milestones/achievements
- No multiple profiles
- No photo uploads
- No notes per entry
- No unit conversion (kg/lbs)
- No month filtering
- No statistics dashboard
- No onboarding flow

Keep it simple, beautiful, and focused.

---

## Success Criteria

✅ Loads user's existing [ww-tracker-data.json](ww-tracker-data.json) perfectly
✅ Beautiful, modern design that looks professional
✅ Fully responsive (mobile to desktop)
✅ Smooth animations and transitions
✅ Dark mode with toggle
✅ Can export/import data easily
✅ Can add/edit/delete entries
✅ Chart visualizes progress clearly

---

*Created: February 9, 2026*
*Data source: ww-tracker-data.json (31 entries, Aug 2025 - Feb 2026)*
