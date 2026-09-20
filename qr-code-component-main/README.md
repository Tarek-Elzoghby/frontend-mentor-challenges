# Frontend Mentor - QR code component solution

This is a solution to the [QR code component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/qr-code-component-iux7YB5QRb). Frontend Mentor challenges help developers improve their coding skills by building realistic projects.

## Table of contents
- Overview
- Screenshot
- Links
- Process & decisions
- Built with
- What I learned
- AI collaboration
- Author

## Overview

### The challenge
Users should be able to:
- View the optimal layout for the component depending on their device's screen size
- See hover states for interactive elements (the two attribution links)

### Screenshot

![QR code component screenshot](./screenshot.jpg)

### Links
- Solution: https://github.com/Tarek-Elzoghby/frontend-mentor-challenges/tree/main/qr-code-component-main
- Live site: not deployed yet — this repo's live demos are routed through a shared hub that's still being set up

## Process & decisions

This wasn't just "type the code" — these are the choices that were actually made, and why.

**Centering the card:** CSS grid with `place-items: center` on the container, over flexbox or absolute positioning. Absolute positioning was ruled out first for breaking on content overflow. Grid was picked over flexbox specifically to practice it, even though flexbox was the more familiar tool for the job.

**Wrapper element:** `main > div.card`, not `main > article`. The card is promotional UI chrome tied to this page, not standalone content that could stand on its own elsewhere — that's the line `article` is for, and this doesn't cross it.

**Internal spacing:** flexbox with `gap`, not margin-per-child or grid. Margin-per-child is harder to adjust from one place. Grid was set aside as more machinery than a single 1D stack needs.

**Footer attribution layout:** flex + gap on the footer container itself, not inline-block on the two paragraph children. The layout decision belongs on the element doing the arranging, not on the elements being arranged — inline-block on the children fought against the earlier choice to give each attribution line its own paragraph.

**A real bug:** two custom properties were both named `--font-heading` — one a color, one a font size — and silently collided, the second overwriting the first with no warning. Fixed by namespacing every custom property by category (`--clr-*`, `--fs-*`, `--fw-*`).

**A real accessibility fail:** Lighthouse flagged a contrast failure. The same muted gray text passed at ~4.55:1 against the white card background but failed at ~3.47:1 against the light blue footer background. Rather than introduce a new color outside the style guide, the footer text was switched to the existing dark heading color, raising contrast to ~9.5:1.

Accessibility was also checked by hand, past what Lighthouse catches automatically: the accessibility tree was inspected to confirm `main` and `footer` register as real landmarks, and keyboard tab order was tested manually to confirm both footer links show a visible focus outline.

## Built with
- Semantic HTML5
- CSS custom properties
- CSS Grid (page centering)
- Flexbox (card and footer layout)
- Mobile-first responsive workflow
- Google Fonts (Outfit, loaded via `<link>` rather than `@import`; trimmed to the two weights actually used — 400 and 700 — instead of the full variable-font range)

## What I learned
Practicing grid for a task flexbox would have handled just as well was worth doing on purpose — the point wasn't the fastest route to done, it was adding a technique to what I reach for next time. Namespacing custom properties by category also isn't optional past a certain size; the `--font-heading` collision cost real debugging time that a naming convention would have prevented from the start.

## AI collaboration
An AI collaborator reviewed the code as it was built — catching bugs, typos, and missing closing tags faster than a manual pass would, and surfacing multiple ways to solve the same problem (grid vs. flexbox vs. absolute positioning for centering, for example) instead of defaulting to whichever one I already knew. The decisions — which option to actually use, and why — were mine; the AI's role was catching mistakes and widening the set of options I was choosing from.

## Author
- GitHub: [@Tarek-Elzoghby](https://github.com/Tarek-Elzoghby)