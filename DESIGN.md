---
name: Monochrome Nutrition
colors:
  surface: '#f7f9fb'
  surface-dim: '#d8dadc'
  surface-bright: '#f7f9fb'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f2f4f6'
  surface-container: '#eceef0'
  surface-container-high: '#e6e8ea'
  surface-container-highest: '#e0e3e5'
  on-surface: '#191c1e'
  on-surface-variant: '#45474c'
  inverse-surface: '#2d3133'
  inverse-on-surface: '#eff1f3'
  outline: '#75777d'
  outline-variant: '#c5c6cd'
  surface-tint: '#545f73'
  primary: '#091426'
  on-primary: '#ffffff'
  primary-container: '#1e293b'
  on-primary-container: '#8590a6'
  inverse-primary: '#bcc7de'
  secondary: '#505f76'
  on-secondary: '#ffffff'
  secondary-container: '#d0e1fb'
  on-secondary-container: '#54647a'
  tertiary: '#1e1200'
  on-tertiary: '#ffffff'
  tertiary-container: '#35260c'
  on-tertiary-container: '#a38c6a'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#d8e3fb'
  primary-fixed-dim: '#bcc7de'
  on-primary-fixed: '#111c2d'
  on-primary-fixed-variant: '#3c475a'
  secondary-fixed: '#d3e4fe'
  secondary-fixed-dim: '#b7c8e1'
  on-secondary-fixed: '#0b1c30'
  on-secondary-fixed-variant: '#38485d'
  tertiary-fixed: '#fadfb8'
  tertiary-fixed-dim: '#ddc39d'
  on-tertiary-fixed: '#271902'
  on-tertiary-fixed-variant: '#564427'
  background: '#f7f9fb'
  on-background: '#191c1e'
  surface-variant: '#e0e3e5'
typography:
  display:
    fontFamily: Plus Jakarta Sans
    fontSize: 40px
    fontWeight: '700'
    lineHeight: 48px
    letterSpacing: -0.03em
  display-mobile:
    fontFamily: Plus Jakarta Sans
    fontSize: 32px
    fontWeight: '700'
    lineHeight: 40px
    letterSpacing: -0.025em
  headline-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 28px
    fontWeight: '700'
    lineHeight: 36px
    letterSpacing: -0.02em
  headline-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 22px
    fontWeight: '600'
    lineHeight: 28px
    letterSpacing: -0.015em
  headline-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 18px
    fontWeight: '600'
    lineHeight: 24px
    letterSpacing: -0.01em
  body-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
    letterSpacing: -0.005em
  body-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
    letterSpacing: 0em
  body-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 16px
    letterSpacing: 0em
  label-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 14px
    fontWeight: '600'
    lineHeight: 20px
    letterSpacing: 0.01em
  label-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 12px
    fontWeight: '600'
    lineHeight: 16px
    letterSpacing: 0.02em
  label-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 11px
    fontWeight: '700'
    lineHeight: 14px
    letterSpacing: 0.04em
  metric-large:
    fontFamily: Plus Jakarta Sans
    fontSize: 36px
    fontWeight: '700'
    lineHeight: 40px
    letterSpacing: -0.03em
  metric-sub:
    fontFamily: Plus Jakarta Sans
    fontSize: 13px
    fontWeight: '500'
    lineHeight: 16px
    letterSpacing: 0.02em
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  gutter: 1rem
  gutter-tablet: 1.5rem
  margin: 1rem
  margin-tablet: 2rem
  margin-desktop: 3rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 1rem
  space-lg: 1.5rem
  space-xl: 2rem
---

## Brand & Style

This design system embodies a disciplined, clinical yet elevated approach to nutritional tracking and macronutrient analytics. Driven by a pure architectural minimalism, it intentionally strips away decorative clutter and saturated lifestyle tropes in favor of editorial clarity, precise typographic rhythm, and immediate data comprehension.

The aesthetic fuses modern high-contrast minimalism with subtle tactile nuances. Surfaces feel crisp, cool, and architectural, creating an atmosphere of focus, restraint, and deliberate personal health control. The interface communicates speed, accuracy, and quiet confidence—treating nutrition metrics not as gamified chores, but as vital personal metrics presented through high-end editorial product design.

## Colors

The palette is strictly monochromatic and cool-toned, eliminating extraneous chromatic distraction so structural hierarchy and data values take absolute precedence.

- **Primary (`#1E293B` - Deep Slate Charcoal)**: Used for primary visual anchors, authoritative text headers, dominant action states, and high-contrast macro indicators.
- **Secondary (`#64748B` - Cool Slate Gray)**: Used for secondary typography, inactive tab labels, metadata, supporting units (e.g., `kcal`, `g`), and subtle iconography.
- **Subtle Border (`#E2E8F0` - Soft Cool Gray)**: Applied to hairline component borders, card perimeters, input field outlines, and divider tracks.
- **Surface Accent / Card Background (`#F8FAFC` - Off-White Slate Tint)**: Grounding tone for modular cards, segmented control track backgrounds, and recessed input fills.
- **Base Canvas (`#FFFFFF` - Crisp Pure White)**: Foundational background providing breathing room, visual hygiene, and high dynamic range.

### Macronutrient High-Contrast Hierarchy
Macronutrient breakdown relies on pure tonal differentiation rather than traditional bright rainbow coding:
- **Protein**: Inverted deep slate badge (`#1E293B` background with `#FFFFFF` text) signaling priority.
- **Karbohidrat (Carbs)**: Outlined cool slate badge (`#FFFFFF` background, `#64748B` label, and `1px` solid `#64748B` border).
- **Lemak (Fat)**: Recessed soft gray badge (`#F1F5F9` background with `#334155` text).

## Typography

Typography is set exclusively in **Plus Jakarta Sans**, utilizing its geometric clarity, balanced counters, and clean contemporary stroke weight. 

- **Macro & Calorie Figures**: Numeric telemetry must render with tabular figures (`tnum`) to maintain structural alignment across dynamic updates and counter transitions.
- **Weights & Densities**: Weight is leveraged functionally: `700` (Bold) for hero numbers and high-impact macro badges; `600` (SemiBold) for structural component headers, control targets, and primary titles; `400` (Regular) for explanatory descriptions and nutritional details.
- **Letter Spacing**: Tight negative tracking is enforced on large titles and calorie values (`-0.03em`) to deliver a compact, architectural presence, while micro labels and badges receive positive tracking (`+0.02em` to `+0.04em`) to ensure instant glanceability at miniature mobile scales.

## Layout & Spacing

The layout is built around a mobile-first, single-column fluid spine that expands systematically into structured grid surfaces on larger displays.

- **Mobile Canvas**: Follows a 4-column layout with a fixed outer screen margin of `1rem` (16px) and internal element gutters of `1rem` (16px). Cards and sections occupy full width within margins, utilizing internal padding of `space-md` (16px) or `space-lg` (24px) for prominent hero widgets.
- **Tablet / Desktop Expansion**: Content scales within a 12-column layout maxing out at `720px` width for dedicated calorie-logging consoles, or `1024px` for comprehensive split-pane dashboard overviews. Gutters expand to `1.5rem` (24px).
- **Rhythm**: All structural margins, heights, and component gaps derive from an immutable 4px/8px base modular unit. Macro summaries and calorie gauges sit within immediate finger reach in the bottom two-thirds of the viewport on handheld devices.

## Elevation & Depth

Visual hierarchy relies on crisp surface layering, low-contrast boundaries, and ultra-diffused ambient shadows rather than dramatic drop shadows.

- **Base Canvas**: Pure `#FFFFFF`.
- **Level 1 (Card & Modular Modules)**: Background `#F8FAFC`, enclosed by a crisp hairline border (`1px solid #E2E8F0`), elevated with an ambient shadow: `0 4px 20px -2px rgba(30, 41, 59, 0.04)`.
- **Level 2 (Floating Action Targets & Segmented Control Knobs)**: Surface `#FFFFFF`, hairline border (`1px solid #E2E8F0`), cast shadow: `0 6px 16px -2px rgba(30, 41, 59, 0.08)`.
- **Level 3 (Modals, Logging Drawers & Bottom Sheets)**: Surface `#FFFFFF`, top border highlight (`1px solid #E2E8F0`), elevated over a backdrop curtain (`rgba(30, 41, 59, 0.35)`) with an ambient vertical shadow: `0 -10px 30px rgba(30, 41, 59, 0.06)`.

## Shapes

The geometric architecture employs a balanced `0.5rem` (8px) core radius, establishing an ergonomic, tactile handfeel without lapsing into toy-like or juvenile softness.

- **Cards and Container Modules**: Standardized to `rounded-lg` (`1rem` / 16px) to frame complex nutritional information gently.
- **Segmented Control Base Track**: `rounded-lg` (`1rem` / 16px), containing an inner slider knob radius of `0.75rem` (12px).
- **Input Fields & Interactive Selectors**: Formed at standard `rounded` (`0.5rem` / 8px).
- **Macro Badges & Navigation Tabs**: Formed as full capsules/pills (`rounded-full` / `9999px`) to create clear semantic differentiation from rectangular modular data cards.

## Components

### Buttons
- **Primary Action**: Deep slate fill (`#1E293B`), text `#FFFFFF`, font weight `600`, height `48px`, border radius `0.5rem` (8px). Active tap scale `0.98` with subtle highlight shift.
- **Secondary Action**: Background `#FFFFFF`, border `1px solid #E2E8F0`, text `#1E293B`, subtle shadow on hover/tap.
- **Ghost Action**: Background transparent, text `#64748B`, hovering or active state transitioning to `#1E293B` text and `#F8FAFC` fill.

### Macro Badges
- Capsule pills (`rounded-full`), padding `4px 12px`, typography `label-sm`.
- **Protein**: `#1E293B` background with `#FFFFFF` text.
- **Karbohidrat**: `#FFFFFF` background, `#64748B` text, `1px solid #CBD5E1` border.
- **Lemak**: `#F1F5F9` background, `#334155` text, without border.

### Progress & Macro Indicators
- **Linear Progress Track**: Track height `6px` or `8px`, background `#E2E8F0`, full pill radius. 
- **Indicator Fill**: Solid `#1E293B` or `#64748B` fill. When multiple macros share a segmented meter, segments are delineated by `2px` `#FFFFFF` separators.
- **Calorie Dial / Donut Gauge**: Base circle track `#E2E8F0` stroke width `8px`; dynamic stroke in `#1E293B` with rounded caps.

### Segmented Controls & Pill Tabs
- **Segmented Control**: Full container recessed in `#F1F5F9` with `4px` internal padding. Selected segment emerges as a `#FFFFFF` raised pill card with `0 2px 8px rgba(30, 41, 59, 0.08)` shadow and `#1E293B` label text. Inactive segments display `#64748B` typography.
- **Pill Tabs**: Unselected tabs have transparent backgrounds and `#64748B` text. Selected tabs feature `#1E293B` fill, `#FFFFFF` text, and crisp spring transitions.

### Input Fields & Search Bars
- Recessed container height `48px`, background `#F8FAFC`, border `1px solid #E2E8F0`, text `#1E293B`, placeholder text `#94A3B8`.
- Focus state activates an immediate boundary shift to `#1E293B` without colored glow halos. Numerical inputs default to tabular formatting.

### Lists & Meal Row Items
- Compact rows featuring horizontal layout: food name and serving size aligned left (`body-md` in `#1E293B`, sub-label in `#64748B`); macro breakdown pills and total calorie value aligned right.
- Separated by clean `1px solid #F1F5F9` horizontal hairlines.

### Cards
- Surface `#F8FAFC`, border `1px solid #E2E8F0`, corner radius `1rem` (16px), internal padding `1.25rem` (20px). Contains clean visual separation between card headers and internal metric grids.