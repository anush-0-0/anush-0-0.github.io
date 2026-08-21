# Ad Safety Notes — read before redesigning

This file exists so future design changes never accidentally break ad monetization.

## The rule
Your site has 4 ad zones, all in `index.html`, each wrapped in a clearly commented block:

1. `#ad-slot-banner` — Banner ad (160×300), inside `<main>`, positioned above the posts list
2. `#ad-slot-native` — Native Banner ad, inside `<main>`, positioned above the posts list
3. Social Bar zone — a script placeholder right after `</footer>`
4. Popunder zone — a script placeholder right after the Social Bar zone

**Never delete or move any of these wrapper comment blocks.**

## A note on Social Bar and Popunder specifically
These two formats behave differently from normal banner ads — they're not boxes on the
page, they're scripts that trigger on their own (Popunder opens a new tab on any click;
Social Bar floats over your content). Keep an eye on how they affect visitor experience
after launch — if bounce rate climbs noticeably, that's usually these two formats being
the cause, not the banner ads.

## Safe to do anytime
- Change colors, fonts, spacing elsewhere on the page
- Add new pages, posts, nav items
- Move the *entire* ad-zone block to a different position in the page (e.g. between posts
  instead of after them) — as long as it stays a direct child of `<main>` and isn't nested
  inside a post card, button, or link

## Never do this
- Don't place a button, link, or clickable element directly touching the ad-zone's edges
  (the `.ad-zone` CSS class already adds 40px margin — don't remove that margin)
- Don't nest the ad code inside a `<button>`, `<a>`, or anything clickable
- Don't delete the Privacy Policy page once one exists (required by AdSense)
- Don't add more than one ad script from more than one network on the same page without
  checking that network's policy on that first

## When adding real ad code
Replace the placeholder text inside `#ad-slot-1` with your ad network's embed script —
nothing else in the file needs to change.
