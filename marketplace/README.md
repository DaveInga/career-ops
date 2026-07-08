# Crate — Music Beat Marketplace (Design Concept)

A single-file HTML design page for a micro-priced music beat marketplace.
Open `index.html` in any browser — no build step, no dependencies, everything
(CSS, JS, SVG icons) is inline.

## What the page shows

- **Sign-in** — modal with passwordless email magic link + "Continue with Google"
  (OAuth 2.0 / OpenID Connect). One account, both doors.
- **Beat browsing** — card grid with tagged-preview players, BPM/key/genre tags,
  and micro-pricing starting at **$0.99**.
- **License tiers** — MP3 lease ($0.99–1.99) → WAV lease ($4.99) →
  trackout/stems ($14.99–24.99) → exclusive ($99+, seller-priced).
- **Payments (Stripe Connect)** — tabbed buyer/seller views:
  - *Buyer:* one-tap checkout, saved cards, and a **wallet credits** system
    ($5/$10/$20 top-ups) so $0.99 purchases aren't eaten by the ~$0.30 fixed
    card fee — many micro-sales batch into one card charge.
  - *Seller:* Stripe Connect **Express** onboarding (~5 min, hosted by Stripe),
    a payout dashboard mock, and transparent fees — each sale is a
    **destination charge** where 90% routes to the seller's Stripe account and
    the platform keeps a 10% `application_fee_amount`. Daily automatic payouts;
    the platform never holds funds or sees bank details.
- **Uploads (Vultr Object Storage)** — drag-and-drop mock plus the real flow:
  1. API issues a **presigned PUT URL** scoped to one object key
  2. Browser uploads **directly** to the S3-compatible endpoint
     (`ewr1.vultrobjects.com`) — multipart for large files, never through the app server
  3. Masters live in a **private bucket**; a worker renders tagged 128kbps
     previews + waveform JSON into a public CDN bucket
  4. Buyers receive short-lived **presigned GET links** after purchase
- **Beyond beats** — other creative goods the same marketplace primitives support.

## Other creative goods for the same marketplace model

The primitives (micro-pricing, instant Stripe Connect payouts, private S3
delivery, license PDFs) generalize to:

| Category | Example pricing |
|----------|-----------------|
| Sample packs & drum kits (per-sound à la carte) | from $0.49/sound |
| Stems & trackouts for remixing/sync | from $2.99 |
| MIDI & chord-progression packs | from $0.99 |
| Synth presets (Serum/Vital) & mixing FX chains | from $1.99 |
| Cover art, album artwork & design commissions | from $4.99 |
| Music video loops, visualizers, lyric-video templates | from $3.99 |
| Lyrics & toplines with demo vocals | from $9.99 |
| Feature verses (vocalist marketplace, delivered as stems) | seller-priced |
| Mixing & mastering services (S3 file handoff, milestones) | from $19.99 |
| SFX libraries for games & film | from $0.99 |
| DAW project files (FL Studio/Ableton templates) | from $6.99 |
| 3D assets, stage visuals & promo AR filters | from $4.99 |

## Implementation notes (for when this becomes real)

- **Auth:** email magic links + Google OAuth via Auth.js/Clerk/Supabase Auth;
  single user record with linked identities, JWT session cookies.
- **Payments:** Stripe Connect Express accounts for sellers; purchases as
  destination charges with `application_fee_amount`; wallet top-ups as ordinary
  PaymentIntents credited to an internal ledger table that funds sub-$1 spends.
- **Storage:** Vultr Object Storage speaks the S3 API, so any AWS SDK works —
  just point the client at the Vultr endpoint. Presigned PUT for uploads,
  presigned GET for delivery, separate private (masters) and public (previews)
  buckets.
