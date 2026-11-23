# Enterprise Design System Specification
## 2. Typography
## 3. Spacing Scale [rem]
## 4. Border Radius [rem]
## 5. Shadow Tokens
## 6. Component Library Specification
## 7. Icon System
## 8. Breakpoints (Responsive)
## 9. Accessibility Standards
## 10. Dark Mode Support
## 11. Design Token Organization (CSS Variables)
## 12. Usage Guidelines

### For Developers
- Import design tokens from `src/styles/tokens.css`
- Use CSS custom properties for theming
- Follow the component library patterns
- Maintain 4.5:1 color contrast minimum

### For Designers
- Use Figma community kit aligned with these tokens
- Follow the spacing and typography scale
- Design with 8px grid system
- Create variants for dark mode

### For Content Authors
- Use heading hierarchy (h1-h6) logically
- Provide descriptive alt text for images
- Maintain line length within 70-80 characters for readability
- Use lists for complex information
```

```css
:root {
  --color-primary-500: #1a1a2e;
  --color-primary-600: #16213e;
  --color-neutral-900: #111113;
  --color-neutral-500: #52525b;
  --radius-md: 0.375rem;
  --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
  --spacing-4: 1rem;
  --font-size-base: 1rem;
  --line-height-normal: 1.5;
}

[data-theme="dark"] {
  --color-neutral-900: #f8f8f2;
  --color-neutral-500: #71717a;
}
```
- **Color tokens** defined for both light and dark variants
- **Prefers-color-scheme:** Automatic system detection
- **Manual toggle:** User can override system preference
- **Consistent experience:** All components adapt to dark mode
- **WCAG 2.1 AA** compliance target
- **Color contrast:** Minimum 4.5:1 for normal text, 3:1 for large text
- **Focus visible:** 2px outline or focus ring with contrast ratio
- **Keyboard navigation:** All interactive elements reachable via Tab, Space, Enter, Escape
- **Screen readers:** Proper ARIA labels, descriptive alt text, logical heading hierarchy
- **Reduced motion:** Respect `prefers-reduced-motion` media query
| Label | Min-width | Description |
|-------|-----------|-------------|
| **xs** | 0px | Mobile, full-width stacking |
| **sm** | 640px | Small mobile phones |
| **md** | 768px | Tablets, iPad portrait |
| **lg** | 1024px | Laptops, small desktop |
| **xl** | 1280px | Desktop, full HD |
| **2xl** | 1536px | Large monitors |
| **3xl** | 1920px | Full HD and above |
- **Set:** Lucide React (consistent line weights)
- **Size:** Inherit from parent, scalable
- **Color:** CurrentColor (neutral 700 or status colors)
- **Common Icons:**
  - User, Users
  - Skill, Skills
  - Project, Projects
  - User-circle, User-check
  - Arrow-up-down, Refresh-cw
  - Calendar, Clock
  - Grid, Layout
  - Bar-chart-2, Pie-chart
  - Shield-check, Lock-open
  - Mail, Phone
  - Folder, Folder-open

### 6.1 Button Component
| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `variant` | "primary" | "secondary" | Style variant: primary, secondary, danger, ghost |
| `size` | "sm" | "md" | Size: sm, md, lg |
| `disabled` | `boolean` | `false` | Disabled state |
| `fullWidth` | `boolean` | `false` | Full width container |
| `asChild` | `boolean` | `false` | Render as child element |

### 6.2 Input Component
| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `type` | "text" | "text" | Input type |
| `placeholder` | `string` | - | Placeholder text |
| `label` | `string` | - | Floating label text |
| `error` | `string` | - | Error message display |
| `disabled` | `boolean` | `false` | Disabled state |
| `required` | `boolean` | `false` | Required field indicator |

### 6.3 Table Component
| Feature | Specification |
|---------|--------------|
| **Responsive** | Horizontal scroll on mobile, horizontal tabs on desktop |
| **Sorting** | Click-to-sort with indicator arrows |
| **Pagination** | Server-side with page size selector |
| **Selection** | Checkbox row selection with bulk actions |
| **Export** | CSV and Excel export functionality |
| **Accessibility** | Keyboard navigation (arrow keys, Home/End), screen reader support |

### 6.4 Card Component
- Padding: responsive (sm: 1rem, md: 1.5rem, lg: 2rem)
- Border: 1px solid Neutral 200
- Border radius: md (6px)
- Shadow: sm (default)

### 6.5 Avatar Component
- Initials fallback when no image provided
- Size: sm (32px), md (48px), lg (64px)
- Fallback color: from primary palette
- **sm:** 0 1px 2px 0 rgba(0, 0, 0, 0.05)
- **DEFAULT:** 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.05)
- **md:** 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06)
- **lg:** 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05)
- **xl:** 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 8px 10px -5px rgba(0, 0, 0, 0.05)
- **2xl:** 0 25px 50px -12px rgba(0, 0, 0, 0.25)
- **none:** 0
- **sm:** 0.125 (2px)
- **DEFAULT:** 0.25 (4px)
- **md:** 0.375 (6px)
- **lg:** 0.5 (8px)
- **xl:** 0.75 (12px)
- **2xl:** 1 (16px)
- **full:** 9999px
- **0:** 0 (0px)
- **1:** 0.25 (4px)
- **2:** 0.5 (8px)
- **3:** 0.75 (12px)
- **4:** 1 (16px)
- **5:** 1.25 (20px)
- **6:** 1.5 (24px)
- **8:** 2 (32px)
- **10:** 2.5 (40px)
- **12:** 3 (48px)
- **16:** 4 (64px)
- **20:** 5 (80px)
- **24:** 6 (96px)

### Font Family
- **Primary:** "Inter", system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif
- **Secondary:** "DM Sans", system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif

### Font Sizes [px]
- **xs:** 12 (0.75rem)
- **sm:** 14 (0.875rem)
- **base:** 16 (1rem) - Body text
- **lg:** 18 (1.125rem)
- **xl:** 20 (1.25rem)
- **2xl:** 24 (1.5rem)
- **3xl:** 30 (1.875rem)
- **4xl:** 36 (2.25rem)
- **5xl:** 48 (3rem)
- **6xl:** 60 (3.75rem)

### Font Weights
- **Light:** 300
- **Regular:** 400
- **Medium:** 500
- **Semi-Bold:** 600
- **Bold:** 700

### Line Heights
- **Tight:** 1.25
- **Normal:** 1.5
- **Relaxed:** 1.75
## Internal Talent Marketplace Platform

## 1. Color Tokens

### Primary Palette
- **Primary 500:** #1a1a2e (Deep midnight blue)
- **Primary 600:** #16213e (Oxford blue)
- **Primary 50:** #e8eaf6 (Lightest blue background)
- **Primary 100:** #f1f3f6 (Light background)

### Secondary Palette
- **Secondary 500:** #0f0f23 (Almost black)
- **Secondary 600:** #0a0a15
- **Secondary 50:** #f8f9fa

### Status Colors
- **Success 500:** #27a74f (Green)
- **Success 50:** #d1e7dd
- **Warning 500:** #ff8c00 (Orange)
- **Warning 50:** #fff4e5
- **Error 500:** #dc2626 (Red)
- **Error 50:** #fecaca
- **Info 500:** #0891b2 (Teal)
- **Info 50:** #cffafe

### Neutral Palette
- **Neutral 900:** #111113 (Darkest text)
- **Neutral 800:** #18181b
- **Neutral 700:** #27272a
- **Neutral 600:** #3f3f46
- **Neutral 500:** #52525b
- **Neutral 400:** #737377
- **Neutral 300:** #a3a3a7
- **Neutral 200:** #d4d4d8
- **Neutral 100:** #f4f4f5
- **Neutral 50:** #fafafa
