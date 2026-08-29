# YouMind upload workflow

Use the current Agent's installed browser-control or computer-use capability. Read that capability's instructions before interacting with the site. Do not hardcode a particular browser product or automation API.

## Authorization states

| User wording | Allowed action |
|---|---|
| Create, edit, test, package, or push a Skill to GitHub | Do not open or publish to YouMind |
| Prepare YouMind listing materials | Generate copy and images; stop before submission |
| Upload, publish, list, or put this Skill on YouMind | Fill the form, submit once, and verify |
| Update this existing YouMind Skill | Open the exact existing listing and edit it; do not create a duplicate |

Never infer publication permission from the mere existence of a Skill or a YouMind screenshot.

## Browser procedure

1. Open the current YouMind creator page from the user's authenticated session.
2. If signed out, pause at login and ask the user to complete authentication. Resume after they confirm.
3. Inspect the live form before filling it. The live labels, validators, accepted file types, and upload limits override cached reference values.
4. Resolve the exact source Skill. If multiple folders or versions could match, identify the intended one before publishing.
5. Fill the fields in the form's visible order. Use the existing Skill instructions as the instruction body; do not replace them with marketing copy.
6. Upload the square avatar and showcase files. Wait for each upload to finish and visually confirm its preview.
7. Re-read all visible fields. Check character limits, missing required fields, malformed image text, and protected source content.
8. Submit exactly once when the request explicitly authorizes publication and the current browser-control policy permits the action. If action-time confirmation is required, ask immediately before submitting.
9. Wait for the resulting success state or listing page. Capture the canonical URL and visible title.
10. If no clear success appears, inspect the page, network-visible error, or validation message before any retry. Never create a second listing to test whether the first one worked.

## Failure handling

- Authentication required: leave the prepared form intact when possible and ask the user to sign in.
- CAPTCHA or human-verification challenge: ask the user to complete it, then resume.
- Terms, licensing, ownership, or other legal attestations: show the exact requirement and ask the user to accept or confirm it; do not attest on their behalf without the required authorization.
- Name collision: prefer editing the existing exact listing when ownership is verified; otherwise ask before renaming or creating another listing.
- Image rejected: follow the live validator, regenerate or convert only the rejected asset, and preserve the approved copy.
- Submission rejected: report the exact validation message and correct only the affected field.
- Browser capability unavailable: deliver the complete upload package and state that form submission is the sole remaining step.
