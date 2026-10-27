# AI video prompt reference

Detailed rules for the [ai-video-prompt skill](SKILL.md). Apply the common rules to create and fix requests; use the failure table when revising and the model notes when a model is named.

## Input decisions

The user can supply two or three Korean lines, optionally a start image, model and duration. A missing model is not a reason to ask. Small missing details can be simply assumed and disclosed. Default to no start image unless one is mentioned; if mentioned but absent, use only the user's description and do not claim to have inspected it.

Ask only when a decision controls the result: conflicting image/scene requirements, missing exact dialogue when speech is the central task, or required events that cannot fit the fixed duration. The budget is two short questions total per request, including follow-ups. If still unresolved, state a conservative assumption or the specific unresolved dependency rather than inventing an answer.

Default length is 8s. Suggest 10s for speech or restrained acting that needs pauses, with the reason in the Korean explanation. Keep an explicit duration unchanged unless the user agrees otherwise. Preserve required people and events; reduce optional actions first. Do not silently rewrite dialogue to make it fit.

For anime I2V, the start frame must already use the desired anime medium. If the provided frame is photographic, explain that a matching drawn frame is needed before that workflow; merely appending `anime` does not resolve the conflict.

## Formula

Write natural English in this order, using about 6–10 useful sentences as a starting point rather than a word limit. Add only detail needed to disambiguate events. Remove drafting placeholders.

```text
One continuous [duration]-second [medium] shot. [Event and tempo.]
[I2V: one preservation sentence. OR T2V: subject, clothes, place,
directional light, starting pose and essential props.]
0–Xs: [Opening state, named actor's action and target's response.]
X–Ys: [Next causal event.]
Y–end: [Readable ending.]
Camera: [shot size, height, one main movement, direction/speed,
what must stay visible].
Sound: [speaker, language and delivery]: "[Exact original dialogue]".
[One or two relevant sounds. Minimal exclusions.]
```

Use non-overlapping major timestamp ranges covering the entire duration. These are approximate directing phases, not frame locks. For Seedance 2.0, also use first/then/finally inside broad phases and explain the timing limit.

## Ten rules

1. **Visible event.** Replace abstract quality claims with what can be seen or heard: a hand catches the rail, shoes meet the roof, a lamp casts a shadow. Extra resolution/lens adjectives do not repair motion.
2. **I2V change.** Preserve identities, clothing, layout and medium in one sentence; spend the rest on motion. Use only the short role labels needed to distinguish people. T2V supplies the missing appearance, light and composition instead.
3. **Continuous shot.** State this at the start and connect the scene with a feasible path through one space. A tracking movement is not a cut. Avoid implicit shot changes in later instructions.
4. **Ownership.** Give every action a stable subject and target, then a visible consequence. Use clothing/role labels consistently. Contact precedes recoil, takeoff precedes landing. Required crowd count remains part of the scene even when optional choreography is simplified.
5. **Positive tempo.** For fast action, start mid-run or mid-fight; specify quick footfalls, short airtime, immediate landing and resumed movement. Remove lengthy opening poses. `No slow motion` alone is not a reliable speed control. Restrained drama can remain still.
6. **Camera path.** Pick a framing and height plus one main motion. Specify direction, speed relative to the actor and what stays visible. Prefer `track right beside her` to equipment-name stacks. Retain mouth/contact/landing visibility when central to the request.
7. **Acting.** Use one immediate intention and one small change per phase. Waiting for a response → gaze lowers slightly. Avoid concurrent crying, grinning, trembling and face-crumpling. State a near-still head or shoulders when it helps keep the performance contained.
8. **Verbatim dialogue.** Quote only the spoken words in their original script and language, preserving punctuation. Put speaker, language, pace, volume and emotion outside quotes. Reserve time for speech and keep the mouth visible. Separate speakers sequentially; do not add translations or romanization as alternative lines.
9. **Matched anime medium.** Anime I2V begins with an already-drawn frame. Preserve clean ink lines, cel colors and drawn backgrounds in positive terms. Avoid contradictory photographic skin/material instructions. A moving perspective can still be 2D animation.
10. **Minimal exclusions.** Describe the desired outcome first. Default exclusions are no background music and no subtitles; honor explicit requests for either. If speech is absent, add `No dialogue.` Use a targeted negative only for a relevant symptom, rather than a universal defect list. Simplify overloaded phases before adding restrictions.

## Model notes

These notes reflect documentation summarized on 2026-10-26, not current UI promises. Use common prose unless the user requests a verified provider format. Do not import another version's limits.

| Model | Relevant adaptation |
|---|---|
| Kling | Positive wording first; minimal sound/text exclusions. Keyframe pins and prose times are different controls. |
| Seedance 2.5 | Realistic phases with few actions; subtitle or texture issues need targeted remedies rather than more detail. |
| Seedance 2.0 | Precise intervals can be unstable: use broad phases plus chronological prose. Styled references matter for anime continuity. |
| MiniMax H3 | Stable speaker IDs/roles; separate delivery from quoted speech. Do not automatically apply provider wrappers to a hosted UI. |
| Wan | Optional negative lists exist in provider workflows; use only relevant exclusions. Silence can be explicit if unwanted speech occurs. Korean accuracy was not established in this kit. |
| Grok | Written timing has no established frame-accuracy guarantee here. Lite 1080p uses upsampling; it is a different variant. Korean accuracy was not established here. |
| FLUX | Keep event load achievable; native-script speech and clear speaker ownership. Higher delivery resolution can use upsampling. Korean accuracy was not established here. |
| Gemini Omni | Explicit continuous shot is especially important. Other languages than English were not evaluated in the cited guide; do not promise Korean accuracy. |
| Veo / other or newer versions | Apply common craft rules. Confirm version-specific length, resolution, audio and controls from current UI/docs rather than guessing. |

## Fix mode

Use the user's symptom and existing prompt. If no output video is supplied, diagnose prompt conflicts directly and label output-level causes as hypotheses. A better prompt is a testable next attempt, not a guaranteed cure.

| Symptom | Inspect | Minimal revision |
|---|---|---|
| Face or wardrobe changes | Conflicting description, changing role names, complex rotation | One preservation line, stable labels, simpler camera where relevant |
| Slow movement | Pose-first opening, long airborne beat, too many events | Start in motion, short causal landings, remove optional beats |
| Wrong dialogue | Direction/translation in quotes, multiple possible speakers, insufficient time | Exact original line, delivery outside quotes, one speaker, reserved speech interval |
| Unexpected cuts | New angles/places described as separate shots, overloaded action | Continuous-shot first line, feasible camera path, fewer optional events |
| Anime becomes realistic | Photo start frame, conflicting realistic materials | Matching anime frame, positive drawn medium, remove contradictory wording |
| Missing people or bad contact | Ambiguous actors, simultaneous choreography | Sequential ownership, contact then reaction, preserve count and show interaction |

Preserve the user's original scene, required count, language and exact line. Return the full revised prompt plus a short change explanation in the two Korean lines. If changing the line or duration is essential, use the question budget; otherwise retain both and identify the limitation.

## Settings and cost

Report model (or unspecified), T2V/I2V, duration, ratio, draft/final resolution, audio and start-frame role. Defaults: 16:9, supported 480p/720p draft, 1080p final, audio on if available. Match I2V source ratio and use the actual start-frame role, not a style-reference slot. Explicit user settings take priority. Verify unsupported/unknown options in the current generation UI.

Suggest cheap drafts and finishing only selected takes. Ordinary low-res generation + upscaling, a new high-res generation, and Seedance 2.5 Draft→1080p are distinct workflows. Include final render/upscale charges, retries and promotional changes. Check the current Generate button; invent no prices and promise no native-quality equivalence. Review faces, contact, line art and original sound before judging sharpness.

## Worked example 1 · I2V Korean dialogue

Input:

```text
카페에서 여자가 상대에게 오늘 대화를 끝내자고 말해요.
"오늘은 여기까지 할게."라고 조용히 말하고 대답을 기다려요.
시작 이미지 있음: 여자는 크림색 카디건, 테이블 앞. 10초, 모델 미정.
```

Prompt:

```text
One continuous 10-second live-action close-up. Continue from the supplied start frame, preserving the woman's identity, clothes, café layout and visual style. She wants the person across the table to accept that the conversation is over.
0–3s: She looks toward the person across the table, keeping her head and shoulders nearly still; her lips gently close as she decides to speak.
3–7s: The woman says in Korean at a quiet, even conversational pace: "오늘은 여기까지 할게." Her mouth remains visible throughout the line.
7–10s: She waits for a reply; when none comes, her gaze lowers slightly and settles.
Camera: eye-level close-up at a fixed distance, with a faint lateral drift that keeps her face and mouth in view.
Sound: her close, dry voice over soft café room tone. She is the only speaker. No background music, no subtitles.
```

상대가 대화를 받아들이길 바라는 의도 하나에, 마지막 시선 변화만 넣었어요.
이미지는 아직 보지 못했으므로, 설명해 주신 인물과 장소만 기준으로 삼았어요.

추천 설정: 모델 미지정 / I2V / 10초 / 16:9(시작 이미지도 같은 비율) / 초안 720p·최종 1080p / 지원 시 오디오 켜기 / 시작 프레임에 이미지 지정. 실제 지원 옵션은 생성 화면에서 확인.

## Worked example 2 · T2V anime motion

Input:

```text
손그림 2D 애니로, 배달부가 옥상의 낮은 난간을 넘고 계속 달려요.
즐거운 느낌, 대사는 없어요. 시작 이미지 없음, 8초, Seedance 2.0.
```

Prompt:

```text
One continuous 8-second hand-drawn 2D animation shot with clean ink outlines, flat cel colors and painted rooftop backgrounds. An adult courier in a red jacket and dark trousers runs left to right toward a low railing, with warm sunlight coming from screen left.
0–3s: First, the courier is already sprinting as the shot opens; the courier plants the right hand on the railing and pushes off the roof with both feet.
3–5s: Then, the courier clears the low railing in a short vault, lands on both feet and immediately takes two quick running steps.
5–8s: Finally, the courier keeps running along the clear rooftop, smiling with delight as the jacket hem follows the movement.
Camera: medium-wide at waist height, tracking right beside the courier at running speed, keeping the hand contact and both feet visible.
Sound: quick footfalls and a brief metallic tap at the railing. No dialogue, no background music, no subtitles.
```

첫 프레임부터 달리게 하고, 낮은 난간 하나와 바로 이어지는 착지로 속도를 표현했어요.
옷과 빛은 간단히 가정했고, Seedance 2.0의 시간 구간은 대략적인 순서 안내예요.

추천 설정: Seedance 2.0 / T2V / 8초 / 16:9 / 초안 720p·최종 1080p / 지원 시 오디오 켜기 / 시작 이미지 없음. 실제 지원 옵션은 생성 화면에서 확인.
