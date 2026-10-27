---
name: ai-video-prompt
description: Write or fix AI video generation prompts from Korean scene briefs for Kling, Seedance, Veo, MiniMax, Wan, Grok, FLUX or Gemini Omni. Use for text-to-video or image-to-video scene direction, dialogue, motion, identity or animation-style troubleshooting.
---

# AI video prompt

Turn a Korean scene brief into a copyable English video prompt, or revise an existing prompt from a reported failure. Preserve the user's event, required people, exact dialogue, medium and chosen settings. Write text and settings recommendations; generating or submitting a video is outside this skill.

## Workflow

1. Identify create or fix mode; extract scene, start-image status, model, duration and dialogue. Ask at most two short questions per request, only for critical ambiguity or conflicting requirements. Otherwise proceed with stated assumptions. Defaults: no start image, live action, 8s, 16:9, no dialogue, audio on where supported, model unspecified.
2. Read [reference.md](reference.md) before drafting or revising. Apply its ten rules, model caveats and relevant failure remedies. It also contains two complete examples. Keep start-image observations separate from the user's unverified description.
3. Draft one continuous shot: format → starting state → timestamped causal phases covering the duration → one main camera move → dialogue/sound → minimal constraints. I2V gets one preservation sentence plus motion; anime I2V needs an already-styled start frame. Use visible actions with an owner and consequence. Acting gets one intention and one small change per phase.
4. In fix mode, distinguish text evidence from an inferred cause; change only what addresses the symptom. Keep exact dialogue and required events. If fitting them needs a changed duration or line, ask within the question budget. Return the whole revised prompt.
5. Check duration coverage, speaker/role consistency, visible contact or mouth, achievable action load and preservation of explicit choices. Treat timing and identity as requested behavior, not a guarantee.

## Output

- One `text` code block containing the complete English prompt; quoted dialogue stays verbatim in its original language, with delivery outside quotes.
- Exactly two Korean explanation lines. Create: design reason + important assumption/check. Fix: `진단:` (mark inference) + `변경:` with a short before → after explanation.
- Recommended settings outside the block: model, T2V/I2V, duration, ratio, draft/final resolution, audio and start-frame role. Honor user choices; recommend available 480p/720p for drafts and 1080p for final. Mark unknown support for UI confirmation.

When helping with cost, separate low-res generation plus upscaling from Seedance 2.5's dedicated Draft→1080p render. Include finishing costs and current Generate-button quotes; do not invent prices or promise equivalent quality.
