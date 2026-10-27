<!-- VIDEO_LINK -->
# AI Video Prompt Kit · Asle's Workroom

A guide, three copyable video prompts, and a prompt generator for learning scene direction and reducing iteration costs.

Made alongside our Korean YouTube video, “8 AI video models, compared with the same prompts.” We used Kling 4.0, Seedance 2.5 and 2.0, MiniMax H3, Wan 3.0, Grok Imagine 1.5, FLUX.3 Video and Gemini Omni Flash 1.1 on Higgsfield.

[한국어 가이드](README.md) · [MIT license](LICENSE)

## What's here

- The guide below: formula, ten rules, model differences and cost tips.
- [Three unchanged final prompts](prompts/README.md): action, breakup drama and anime parkour.
- [Paste-in generator](generator/GENERATOR_PROMPT.md) and [agent skill](skills/ai-video-prompt/SKILL.md). Both take Korean briefs and return English prompts with Korean explanations.

## A copyable formula

```text
FORMAT: One continuous [duration]-second [live-action / hand-drawn 2D] shot.
START: I2V — one line preserving people, clothes, setting and medium.
       T2V — subject, clothes, place, directional light and starting pose.
ACTION: Already [doing X] → A acts on B → B responds → readable ending.
        Divide into broad phases: 0–3s / 3–6s / 6–8s.
CAMERA: Shot size + height + one main movement + what stays visible.
SOUND: Speaker + language + delivery outside quotes. "Exact original line."
       One or two ambient/action sounds.
KEEP: Only essential constraints. No subtitles, no background music.
```

I start with roughly 6–10 useful sentences and cut anything that does not change an observable result. Times are directing cues, not guaranteed frame locks.

## Ten rules I use

These combine provider advice with directing choices; they are not universal success guarantees.

1. **A visible event.** I replace `Epic masterpiece` → `She runs across wet pavement under a streetlamp.`
2. **Change from the I2V image.** `Long redesign of her face and outfit` → `Preserve the start frame; she turns toward the door.` Short clothing labels can still distinguish people.
3. **Explicit continuity.** `Run, landing, close-up` → `One continuous shot; the camera approaches her after landing.` Omni's guide explicitly describes a multi-shot default. [Google guide](https://ai.google.dev/gemini-api/docs/omni)
4. **An owner and consequence for each action.** `They fight fiercely` → `The gray-hoodie man swings; she blocks; he stumbles back.`
5. **Fast action already in motion.** `No slow motion, epic jump` → `Already sprinting, she clears a low rail and immediately takes two more steps.`
6. **Camera travel rather than equipment lists.** `FPV drone, orbit, zoom` → `Waist-high medium-wide; track right beside her, keeping both feet visible.`
7. **One intention, one small change.** `Cry, tremble, grin and collapse` → `She waits for his answer; when none comes, her gaze lowers slightly.`
8. **Speech separate from delivery.** `"Sadly: 그만하자, 이제. Let's stop."` → `She says in Korean, quietly: "그만하자, 이제."` I leave speaking time and keep the mouth visible.
9. **A matching anime reference.** `Photo + anime` → `Already-drawn 2D start frame + preserve its ink lines and cel colors during motion.` Seedance 2.0 documents reference-style drift. [BytePlus guide](https://docs.byteplus.com/en/docs/ModelArk/seedance-2-0-prompt-guide)
10. **Positive result first, few negatives.** `No bad hands, low quality, errors…` → `Her hand plants on the rail; the landing stays visible. No subtitles, no background music.` I reduce overloaded action before adding restrictions.

## Model differences

Documentation snapshot through October 26, 2026. Provider capabilities may differ from Higgsfield controls. “Not established” does not mean impossible.

| Model | Timing / exclusions | Speech and practical caveat |
|---|---|---|
| Kling 4.0 | Time progression; up to 10 keyframes. Discourages negatives except relevant text/music exclusions. | Korean listed. Keyframe pins differ from written times. |
| Seedance 2.5 | Realistic intervals, one-second units suggested; positive-first wording. | Korean listed. Overloaded intervals can omit actions or introduce cuts. |
| Seedance 2.0 | Precise ranges can be unstable; chronological prose helps express order. | Official Korean example. Match anime reference medium. |
| MiniMax H3 | Provider timing format is shot-based; no blanket negative stance established. | Korean among 11 languages. Keep speaker IDs stable. |
| Wan 3.0 | Timed-shot formula; optional negative list. | Korean validation not established. Explicit silence can address unwanted speech. |
| Grok Imagine 1.5 | No prose frame-accuracy guarantee or negative contract established here. | Korean validation not established. Lite 1080p is upsampled 720p. |
| FLUX.3 Video | Timelines; 2–3 achievable beats suggested for 5s; targeted exclusions. | Native-script dialogue advice; no Korean benchmark here. Higher delivery resolutions use upsampling. |
| Gemini Omni Flash 1.1 | Natural-language timecodes; exclusions in prose. | Non-English languages not evaluated. Explicitly request one shot; listen to Korean output. |

The [source list](README.md#출처) contains the provider guides behind this table.

## Saving money

**As of October 26, 2026 on Higgsfield; subject to change.** This preserves the dated **10-second I2V Generate-button snapshot**, in Higgsfield credits. A dash means no price listed here. Variant, mode, inputs and promotions matter.

| Model / variant | 480p | 720p | 1080p | Pre-discount 1080p | Notes |
|---|---:|---:|---:|---:|---|
| Kling 4.0 | — | 5 | 10 | 40 | 75% promotion at the time |
| Seedance 2.5 | 30 | 70 | 160 | — | 480p Draft also displayed 30; check final-stage charge |
| Seedance 2.0 | 30 | 45 | 120 | — | 4K: 220 |
| MiniMax H3 Standard | — | — | — | — | 2K: 20, previously 40; Max: 480p 15 / 768p 25 |
| Wan 3.0 Prime | 15 | 30 | 60 | 77 | Regular Wan 3.0 1080p: 35 |
| Grok Imagine 1.5 | 25 | 45 | 80 | — | Lite 1080p: 40, upsampled |
| FLUX.3 Video | — | 60 | 80 | — | 4K: 130 |
| Gemini Omni Flash 1.1 | — | 30 | 45 | — | 360p: 10 / 4K: 90 |

The button snapshot can differ from older blog examples. Higgsfield's [changelog](https://higgsfield.ai/creator-hub/changelog) notes the temporary Kling launch discount and points to the Generate button for the actual quote.

- **I draft cheaply and finish selected takes.** Seedance 2.5's 10s 480p is 30 versus 160 at 1080p in this snapshot. It helps to review motion, dialogue and faces before increasing resolution.
- **Low-res plus upscale is worth a short trial.** I include the upscale fee. Faces and line art can shimmer; enlargement cannot fix wrong contact or acting, and native-1080p equivalence is not established.
- **I treat Draft Mode separately.** Seedance 2.5's dedicated workflow makes a 480p preview, then a selected 1080p render. It differs from enlarging a finished MP4. Both charges and the final performance need review. [Draft announcement](https://higgsfield.ai/creator-hub/changelog)
- **I use 8s when sufficient.** In the supplied survey, matched 8s jobs cost 80% of 10s: Seedance 2.5 1080p was 128 versus 160. Rounding/minimums can differ in the current mode. The [official 8s table](https://higgsfield.ai/blog/seedance-2-5-pricing-2026) also lists 24/56/128, but uses T2V conditions.
- **I check the Generate button after every setting change.** Promotions expire; muting does not necessarily halve the cost.
- **I count retries and finishing.** Five ordinary 480p trials plus one new 1080p generation cost `5×30+160=310`, versus `5×160=800`, about 61% less if the final succeeds. This does not price the dedicated Draft upgrade or guarantee a matching take.

## Prompts from the video

- [1v6 alley action](prompts/01_action_1v6_alley.txt): seven-person continuity, contact, reactions and fast camera movement.
- [Breakup close-up](prompts/02_drama_breakup_closeup.txt): restrained facial changes, exact Korean speech and lip-sync.
- [Anime rooftop parkour](prompts/03_anime_rooftop_parkour.txt): drawn-style continuity, obstacle transitions and landings.

[Settings and frame notes](prompts/README.md): 16:9, 1080p target, audio on, start-frame I2V; 8s action, 10s drama/anime. Available resolution varies by variant. Start frames will be added later; they are not included yet, so the text alone cannot reproduce the comparison conditions. The original prompts are denser than the beginner generator examples.

## Using the generator

**Paste-in:** you can copy all of [GENERATOR_PROMPT.md](generator/GENERATOR_PROMPT.md) into the first message of a new ChatGPT, Claude or Gemini chat, or a system-instructions field when available. Two or three Korean lines describing the scene are enough; start-image status, model and length are optional.

You receive an English prompt in one code block, exactly two Korean explanation lines, and recommended settings. It asks at most two short questions only when critical. To fix a prompt, paste it with a symptom such as `얼굴이 바뀌어요` (face changes), `동작이 느려요` (motion is slow), or `대사가 이상해요` (dialogue is wrong).

**Claude Code / agent skill:** from the downloaded repository folder, this command copies both files into Claude Code's personal skills directory:

```sh
mkdir -p ~/.claude/skills/ai-video-prompt
cp skills/ai-video-prompt/SKILL.md skills/ai-video-prompt/reference.md ~/.claude/skills/ai-video-prompt/
```

You can invoke `/ai-video-prompt` with your scene in Claude Code; the personal path and invocation follow the [official skills documentation](https://code.claude.com/docs/en/skills). For another agent, the entire [skill folder](skills/ai-video-prompt/) goes in that tool's skills location. Both [SKILL.md](skills/ai-video-prompt/SKILL.md) and [reference.md](skills/ai-video-prompt/reference.md) are needed.

The actual length, aspect ratio, resolution, audio and image role also need matching settings in the generation UI.

## Sources

The [compact bibliography of all 54 sources](README.md#출처) gives linked titles for provider documentation, Higgsfield guidance, upscalers and practitioner comparisons. Research cutoff: October 26, 2026. Vendor documentation describes capabilities, not measured success rates. Reddit evidence was search-indexed; some video evidence used earlier transcript research or secondary summaries. Older-model examples inform direction, not current-model rankings.
