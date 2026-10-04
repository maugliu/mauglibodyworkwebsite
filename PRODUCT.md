# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

Primary: Russian-speaking people living in Tbilisi — relocants, IT and office workers, remote workers — with back, neck or lower-back pain (acute or chronic), tension and fatigue that sleep doesn't fix, trouble switching off, and a wish to deal with the cause rather than mute symptoms. Some also want to understand their own body better.

Equally real: English-speaking clients in Tbilisi (expats, internationals). The EN version (`en/`) serves them and is a full audience, not an afterthought.

Separate segment: women after childbirth — the postnatal recovery format (2×90 min).

Job: find a trustworthy specialist, understand which format fits, see the price, and book a session — usually by moving into the Telegram bot.

## Product Purpose

Maugli Bodywork is the practice of Ivan "Maugli" — massage therapist, kinesiologist, body practitioner in Tbilisi. The site explains the approach, presents the formats and prices, builds trust, and routes visitors to booking. Success = a booked session (most often via @maugli_bodywork_bot).

## Positioning

- **Diagnosis before work.** Every session starts with assessment: conversation, visual diagnostics, manual muscle testing. Only then the hands-on work, with tools chosen for the request.
- **Cause, not symptom.** The goal is to find and work with the source of pain or tension. Evidence-minded, no esoterics, with respect for the client's boundaries.

## Operating Context

- Visitors arrive largely via Telegram, Instagram, QR codes and word of mouth; mostly on phones.
- Booking funnel: site → Telegram bot (@maugli_bodywork_bot) → time slot. Services pages show live open slots synced with the bot; slots are pure time, not tied to formats.
- Promo / QR mechanics (`?promo=first`, −15% first session, leads fixed for 14 days) are run by Maugli personally.
- Bilingual: RU at root, EN under `en/`. Journal posts in `journal/` and `en/journal/`.

## Capabilities and Constraints

- Static HTML/CSS/JS, no frameworks or build tools; hosted on Cloudflare Pages from GitHub. Each page is self-contained (CSS in `<style>`, JS in a deferred script).
- Six formats (source of truth: `services.html` and CLAUDE.md): Intro Session, Kinesio·Focus, Bodywork, Kinesio·Full, Kinesiotaping, Postnatal recovery. Prices in GEL.
- Pages `promo.html`, `gift.html`, `staya_promo.html`, `admin.html`, `webinar-tejp.html` are noindex / not in nav. `webinar-tejp.html` deliberately sits outside the site's design system.
- Fixed decisions recorded in CLAUDE.md (fonts, dark theme default, always-dark nav, grain overlay, removed features that must not return) bind all future work.

## Brand Commitments

- Name: Maugli Bodywork; practitioner: Иван «Маугли» / Ivan Maugli.
- Voice (RU): informal «ты» on the main pages, warm, direct, plain-spoken; no esoterics, no medical overclaiming. Core line: «Тело знает. Нужно лишь научиться слушать.»
- Personal story is part of the brand: back pain since 19, found the way through touch, anatomy and muscle testing.

## Evidence on Hand

- Stats on the site are real and conservative (actual numbers are higher): 2500+ hours of practice, 300+ clients, practicing since 2020, 6+ years. Update upward only with figures from Maugli; never invent them.
- Real client testimonials (e.g. Ира Логинова) shown as message bubbles on the homepage.
- Certificates: Vector Massage I & II (2020, 2021), Kinesiology — pelvis/lower limbs and shoulder girdle (2020), Postnatal recovery — Dr. Krutov school / NL-School (2022). Scans: `massage_certificate01–05.webp`.
- Photography: `hero`, `portrait`, `approach`, format photos (`kinesio`, `bodypractice`, `taping`, `postnatal`, `consultation`), `cta_hands`, `diag2/3`.
- Absent: medical credentials, clinical studies, press. Do not fabricate.

## Product Principles

1. Trust before persuasion: show the method, the person and real proof; never hype.
2. Cause over symptom — in copy and in structure (explain the diagnostic step first).
3. The shortest honest path to booking: format → price → free slot → bot.
4. RU and EN are equal citizens; every change ships to both.
5. Phone first: most visitors come from Telegram/Instagram on mobile.
