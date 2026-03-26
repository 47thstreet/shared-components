# TB Group Shared Components

Reusable Astro components for the TB Group ecosystem. Each component is self-contained and copy-pasteable into any Astro project with Tailwind CSS.

## Components

### EventCard

Displays an event with image, date, venue, price, and ticket link.

```astro
---
import EventCard from '../components/EventCard.astro';
---

<EventCard
  name="Summer Rooftop"
  date="2026-07-15"
  time="10:00 PM"
  venue="Somewhere NYC"
  imageUrl="/flyer.jpg"
  ticketUrl="https://kartis-astro.vercel.app/en/event/summer-rooftop"
  price="$25"
  featured={true}
  accentColor="#a78bfa"
/>
```

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `name` | `string` | required | Event name |
| `date` | `string` | required | ISO date string |
| `time` | `string` | - | Display time |
| `venue` | `string` | - | Venue name |
| `location` | `string` | - | City/area |
| `imageUrl` | `string` | - | Flyer/cover image URL |
| `ticketUrl` | `string` | - | Link to ticket purchase |
| `price` | `string` | - | Price display string |
| `featured` | `boolean` | `false` | Show featured badge |
| `accentColor` | `string` | `#a78bfa` | Accent color for CTA |

### TicketButton

A styled CTA button for ticket purchases with three variants.

```astro
---
import TicketButton from '../components/TicketButton.astro';
---

<TicketButton href="https://kartis-astro.vercel.app/en/event/my-event" />
<TicketButton href="/checkout" label="Reserve Table" variant="outline" size="lg" />
<TicketButton href="/checkout" variant="solid" accentColor="#34d399" />
```

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `href` | `string` | required | Link URL |
| `label` | `string` | `Get Tickets` | Button text |
| `variant` | `solid \| outline \| ghost` | `solid` | Visual style |
| `size` | `sm \| md \| lg` | `md` | Button size |
| `accentColor` | `string` | `#a78bfa` | Brand color |
| `fullWidth` | `boolean` | `false` | Full width mode |
| `disabled` | `boolean` | `false` | Disabled state |
| `newTab` | `boolean` | `true` | Open in new tab |

### PromoterBadge

Displays a promoter's name, tier, and stats. Has compact (inline) and full (card) modes.

```astro
---
import PromoterBadge from '../components/PromoterBadge.astro';
---

<!-- Full card -->
<PromoterBadge name="Alex M." tier="gold" ticketsSold={142} commission={0.15} />

<!-- Compact inline -->
<PromoterBadge name="Sarah K." tier="platinum" ticketsSold={500} compact={true} />
```

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `name` | `string` | required | Promoter name |
| `tier` | `bronze \| silver \| gold \| platinum` | `bronze` | Tier level |
| `ticketsSold` | `number` | `0` | Total tickets sold |
| `commission` | `number` | - | Commission rate (0-1) |
| `avatarUrl` | `string` | - | Avatar image URL |
| `promoCode` | `string` | - | Promo code to display |
| `compact` | `boolean` | `false` | Inline badge mode |

### CountdownTimer

A live countdown to a target date/time. Pure vanilla JS -- no React or Vue required.

```astro
---
import CountdownTimer from '../components/CountdownTimer.astro';
---

<CountdownTimer targetDate="2026-07-15T22:00:00" />
<CountdownTimer
  targetDate="2026-12-31T00:00:00"
  label="New Year's Eve"
  expiredText="Happy New Year!"
  accentColor="#00d4ff"
  compact={true}
/>
```

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `targetDate` | `string` | required | ISO datetime string |
| `label` | `string` | - | Label above countdown |
| `expiredText` | `string` | `Event has started!` | Text shown when expired |
| `accentColor` | `string` | `#a78bfa` | Border accent color |
| `compact` | `boolean` | `false` | Smaller display mode |

## Installation

Copy any component file from `src/components/` into your Astro project's `src/components/` directory. No npm install required.

```bash
cp ~/ecosystem/shared-components/src/components/EventCard.astro ~/ecosystem/my-project/src/components/
```

## Requirements

- Astro 4+
- Tailwind CSS

## Design System

All components follow the TB Group dark theme:

- Background: `#0a0a0a` / `#111111` (surface)
- Foreground: `#fafafa`
- Muted: `#737373`
- Accent: `#a78bfa` (violet, customizable via `accentColor` prop)
- Font: Inter (body), Playfair Display (display)
