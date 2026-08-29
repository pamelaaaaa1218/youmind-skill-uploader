# Baseline findings

## Scenario

An independent Agent was asked to upload an existing retro-magazine-cover Skill to YouMind, generate its required listing assets, avoid provider-specific APIs, and finish the publication rather than stopping at advice.

## Observed failures without this Skill

- It stopped to request the full prompt instead of completing all inferable work.
- It invented fields absent from the supplied creator form, including price, tags, visibility, version, and editorial recommendation.
- It proposed a 4:3 showcase image instead of the current 16:9 detail-cover convention.
- It provided image prompts but did not generate the requested bitmap assets.
- It proposed a large handoff structure that obscured the seven actual backend fields.
- It stopped at a handoff package and never operated or submitted the YouMind creator form.
- It did correctly avoid API keys and specific image providers; that behavior must be preserved.

## Behaviors the Skill must change

1. Complete the seven real fields first.
2. Use 1:1 for the avatar and 16:9 for the cover/showcase by default.
3. Generate assets through the current Agent's image skill instead of stopping at prompts.
4. Ask only when a missing decision is genuinely blocking.
5. Keep provider and API details out of the reusable workflow.
6. Open the live creator, submit once, and verify the published listing when upload was explicitly requested.
