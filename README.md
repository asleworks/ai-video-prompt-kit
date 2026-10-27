# AI 영상 프롬프트 키트 · Asle's Workroom

영상: [AI 영상 모델, 싹 다 비교해봤습니다](https://www.youtube.com/watch?v=jgO1ThnRDV8)

AI 영상 프롬프트를 복사해 보고, 직접 고치고, 시행착오 비용을 줄이기 위한 한국어 키트예요.

「AI 영상 모델 8개, 같은 프롬프트로 싹 다 비교」를 만들며 정리했어요. Kling 4.0, Seedance 2.5·2.0, MiniMax H3, Wan 3.0, Grok Imagine 1.5, FLUX.3 Video, Gemini Omni Flash 1.1을 Higgsfield에서 비교했어요.

[English](README.en.md) · [MIT 라이선스](LICENSE)

## 이 저장소에 있는 것

- **가이드:** 이 페이지의 공식 카드, 규칙 10개, 모델 차이와 비용 팁
- **영상에 쓴 프롬프트 3개:** [액션·드라마·애니 최종본](prompts/README.md)
- **프롬프트 생성기:** [챗봇에 붙여넣는 버전](generator/GENERATOR_PROMPT.md) / [에이전트 스킬](skills/ai-video-prompt/SKILL.md)

처음이라면 아래 카드를 복사해 빈칸을 채워 보면 좋아요. 영어로 옮기는 게 번거로우면 생성기에 한국어로 두세 줄만 적어도 돼요.

## 프롬프트 공식 · 한 장 카드

```text
① 형식: 한 컷 연속 [초]초, [실사 / 손그림 2D 애니]. 장면을 한 문장으로.
② 시작: 이미지→영상이면 인물·옷·장소·화풍을 유지하는 문장 하나.
         텍스트→영상이면 인물·옷·장소·빛·시작 자세를 짧게.
③ 동작: 시작부터 [누가 무엇을 하는 중] → [A의 행동] → [B의 반응] → [끝 모습].
         [0–3초] / [3–6초] / [6–8초]처럼 큰 구간에 나누기.
④ 카메라: 샷 크기 + 높이 + 주된 움직임 하나 + 계속 보여야 할 것.
⑤ 소리: 말하는 사람 + 언어 + 말투. "대사 원문 그대로". 효과음 한두 개.
⑥ 지킬 것: 꼭 필요한 조건만 짧게. 자막 없음, 배경음악 없음.
```

저는 6~10문장 정도로 시작해요. 눈에 보이거나 들리는 결과를 바꾸지 않는 문장은 덜어내면 좋아요. 시간 구간은 흐름을 나누는 안내라, 초 단위 실행을 보장하지는 않아요.

## 제가 쓰는 규칙 10개

아래는 공식 문서의 공통 조언에 제 연출 요령을 더한 기준이에요. 모든 모델에 똑같이 통하는 정답은 아니에요.

### 1. 추상적인 칭찬보다 눈에 보이는 사건

누가 무엇을 하고, 빛이 어디서 오는지 쓰면 장면을 확인하기 쉬워요.

아쉬운 예: `에픽하고 영화 같은 걸작.` → 바꾼 예: `가로등 아래, 여자가 젖은 바닥을 딛고 오른쪽으로 달린다.`

### 2. 시작 이미지가 있으면 변화에 집중

이미 있는 얼굴과 옷을 길게 다시 설명하기보다, 유지 문장 하나 뒤에 움직임을 적으면 좋아요. 여러 사람이 있으면 옷으로 구분하는 짧은 설명은 도움이 돼요.

아쉬운 예: `갈색 눈, 긴 머리, 코와 입 모양은…` → 바꾼 예: `시작 프레임의 인물·옷·장소를 유지한다. 여자가 문 쪽으로 고개를 돌린다.`

### 3. 한 컷이라는 조건을 첫 문장에

저는 `One continuous 8-second shot`처럼 시작해요. 특히 Omni는 한 컷을 말하지 않으면 여러 샷으로 이야기를 구성하려는 기본 동작이 있다고 안내해요. [Google 안내](https://ai.google.dev/gemini-api/docs/omni)

아쉬운 예: `달리고, 착지하고, 얼굴 클로즈업.` → 바꾼 예: `한 컷 연속 8초. 착지 후 카메라가 끊김 없이 얼굴로 다가간다.`

### 4. 동작마다 주인과 반응

인물 이름이 없어도 `회색 후드 남자`, `검은 재킷 여자`처럼 고정하면 좋아요. 행동 뒤에 상대에게 생긴 결과도 붙여요.

아쉬운 예: `둘이 격렬하게 싸운다.` → 바꾼 예: `회색 후드 남자가 오른손을 휘두른다. 여자가 왼팔로 막고, 남자가 한 걸음 밀려난다.`

### 5. 빠른 장면은 이미 움직이는 상태에서

저는 시작 포즈를 길게 두지 않고, 짧은 체공과 바로 이어지는 착지를 적어요. `슬로모션 금지`만으로 속도가 해결되지는 않아요.

아쉬운 예: `슬로모션 절대 금지. 멋지게 점프.` → 바꾼 예: `첫 프레임부터 달리고 있다. 낮은 난간을 넘고, 발이 닿자마자 두 걸음을 더 달린다.`

### 6. 카메라는 장비보다 이동 경로

샷 크기와 높이를 고른 뒤, 주된 움직임 하나를 적으면 좋아요. 좌우는 시작 화면 기준으로 정하고, 접촉이나 착지처럼 중요한 부분을 계속 보이게 해요.

아쉬운 예: `FPV 드론, 오빗, 줌, 핸드헬드.` → 바꾼 예: `허리 높이의 미디엄 와이드. 오른쪽으로 같은 속도로 따라가며 두 발과 착지를 보여준다.`

### 7. 연기는 의도 하나 + 작은 변화 하나

`슬프다`보다 지금 상대에게 무엇을 바라는지 정하면 좋아요. 한 구간에 울음·떨림·웃음을 모두 넣기보다 작은 변화 하나를 고르면 덜 과장돼요.

아쉬운 예: `울고 떨고 찡그리고 웃으며 무너진다.` → 바꾼 예: `그의 대답을 기다린다. 대답이 없자 시선이 조금 내려간다.`

### 8. 대사 원문과 말투를 분리

한국어 대사는 한글 그대로 두고, 말하는 사람과 말투는 따옴표 밖에 적어요. 말할 시간과 입이 보이는 구도도 남겨 두면 좋아요.

아쉬운 예: `"슬프게: 그만하자, 이제. Let's stop."` → 바꾼 예: `She says in Korean, quietly and evenly: "그만하자, 이제."`

### 9. 애니는 시작 그림부터 같은 애니 화풍

이미지→영상이라면 시작 이미지가 목표 화풍과 맞는지 먼저 봐요. Seedance 2.0 문서도 실사 참고 이미지가 애니를 실사 쪽으로 끌 수 있다고 설명해요. [Seedance 안내](https://docs.byteplus.com/en/docs/ModelArk/seedance-2-0-prompt-guide)

아쉬운 예: `실사 사진 + anime 한 단어.` → 바꾼 예: `같은 2D 애니 시작 그림 + 선화·셀 채색을 유지하며 달리고 착지한다.`

### 10. 원하는 결과를 먼저, 금지 조건은 짧게

저는 공통 프롬프트에는 꼭 필요한 자막·음악 제외 정도만 남겨요. 한 구간에 동작을 너무 많이 넣었다면 금지어를 늘리기 전에 동작 수부터 줄여 보면 좋아요.

아쉬운 예: `나쁜 손 금지, 저품질 금지, 오류 금지…` → 바꾼 예: `한 손으로 난간을 짚고 넘는다. 착지가 보인다. 자막 없음, 배경음악 없음.`

## 모델별로 다른 점

2026년 10월 26일까지 정리한 문서 기준이에요. 공급사 기능과 Higgsfield에서 실제 보이는 설정은 다를 수 있어요. `확인 안 됨`은 불가능하다는 뜻이 아니에요.

| 모델 | 시간 지시 | 금지 조건 | 한국어 대사 | 제가 챙기는 점 |
|---|---|---|---|---|
| Kling 4.0 | 시간 흐름·최대 10개 키프레임 안내 | 부정 지시 비추천, 자막·음악 제외는 가능 | 공식 지원 언어 | 키프레임 고정과 문장 속 시간은 다른 기능이에요 |
| Seedance 2.5 | 1초 단위·현실적인 구간 권장 | 원하는 결과 먼저, 필요한 제외 가능 | 공식 지원 언어 | 한 구간의 동작 과밀은 누락·컷으로 이어질 수 있어요 |
| Seedance 2.0 | 정확한 구간은 불안정할 수 있음 | 긴 목록보다 필요한 조건 | 공식 한국어 예시 있음 | 시간 순서와 시작 이미지의 화풍을 우선 봐요 |
| MiniMax H3 | 공식 형식은 컷 단위 시간 | 일괄 금지·허용 입장 확인 안 됨 | 11개 지원 언어에 포함 | 화자를 같은 이름이나 ID로 유지해요 |
| Wan 3.0 | 시간 표시가 있는 샷 공식 | 별도 금지 목록 지원 | 한국어 검증 확인 안 됨 | 원치 않는 발화가 생기면 `No dialogue`를 짧게 붙여요 |
| Grok Imagine 1.5 | 문장 시간의 정확도 보장 확인 안 됨 | 전용 규칙 확인 안 됨 | 한국어 검증 확인 안 됨 | Lite의 1080p는 720p 업샘플이에요 |
| FLUX.3 Video | 타임라인 지원, 5초에 2~3개 동작 제안 | 필요한 대상만 제외 | 원문 언어 대사 안내, 한국어 검증 없음 | 높은 출력 해상도에는 업샘플링이 쓰여요 |
| Gemini Omni Flash 1.1 | 자연어 시간·타임코드 지원 | 별도 칸 없이 문장으로 제외 | 영어 외 언어는 평가되지 않음 | 한 컷을 명시하고 한국어 소리를 직접 들어봐요 |

표는 아래 공식 문서 묶음에서 요약했어요. 문장 속 시간은 정확한 프레임 고정과 달라요. Seedance 2.0에서는 시간 표기를 큰 구간으로 줄이고 `first / then / finally` 순서를 함께 쓰면 좋아요.

## 돈 아끼는 법

### 생성 버튼 가격표

**2026년 10월 26일 Higgsfield 기준, 바뀔 수 있음**

당일 이미지→영상 화면에서 확인해 정리한 **10초 생성 비용, 단위는 Higgsfield 크레딧**이에요. `—`는 해당 해상도 가격을 이 표에 적지 않았다는 뜻이에요. 할인·모드·입력 조건이 다르면 달라질 수 있어요.

| 모델·등급 | 480p | 720p | 1080p | 할인 전 1080p | 비고 |
|---|---:|---:|---:|---:|---|
| Kling 4.0 | — | 5 | 10 | 40 | 당시 75% 할인 |
| Seedance 2.5 | 30 | 70 | 160 | — | 480p Draft 표시도 30, 최종 단계 비용은 별도 확인 |
| Seedance 2.0 | 30 | 45 | 120 | — | 4K 220 |
| MiniMax H3 Standard | — | — | — | — | 2K 20, 할인 전 2K 40. Max: 480p 15 / 768p 25 |
| Wan 3.0 Prime | 15 | 30 | 60 | 77 | 일반 Wan 3.0의 1080p는 35 |
| Grok Imagine 1.5 | 25 | 45 | 80 | — | Lite 1080p는 40, 업샘플 출력 |
| FLUX.3 Video | — | 60 | 80 | — | 4K 130 |
| Gemini Omni Flash 1.1 | — | 30 | 45 | — | 360p 10 / 4K 90 |

표의 당일 화면 가격과 블로그의 게시 시점 가격은 다를 수 있어요. Kling의 한시 할인과 Generate 버튼 확인은 [Higgsfield 변경 기록](https://higgsfield.ai/creator-hub/changelog)에도 안내되어 있어요. 같은 설정에서 **Generate 버튼에 표시된 숫자**를 마지막 기준으로 보면 좋아요.

### 저는 이렇게 비용을 줄여요

- **초안은 낮은 해상도부터.** Seedance 2.5는 위 10초 표에서 480p 30, 1080p 160이에요. 동선·대사·표정이 괜찮은지 먼저 보고 최종 해상도로 옮기면 좋아요.
- **저해상도 + 업스케일도 짧게 시험.** 480p나 720p 결과를 업스케일하면 비용을 줄일 여지가 있어요. 다만 얼굴·선화가 일렁일 수 있고, 틀린 접촉이나 연기를 복구해 주지는 않아요. 생성비와 업스케일비를 합쳐 비교해요.
- **Seedance 2.5 Draft 모드는 따로 구분.** 480p 초안을 고른 뒤 1080p로 렌더하는 두 단계 기능이에요. 완성 MP4를 키우는 업스케일과 달라요. 초안과 최종 비용을 각각 보고, 최종 표정·움직임도 다시 확인하면 좋아요. [Draft 모드 안내](https://higgsfield.ai/creator-hub/changelog)
- **8초면 되는 장면은 8초로.** 위 조사에서는 같은 조건의 8초가 10초 비용의 80%였어요. 예를 들어 Seedance 2.5 1080p는 128 대 160이에요. 다른 모드의 최소 길이·반올림은 버튼에서 확인하면 좋아요. 공식 블로그의 8초 가격도 [같은 24 / 56 / 128](https://higgsfield.ai/blog/seedance-2-5-pricing-2026)이지만, 그 글은 텍스트→영상 조건이에요.
- **할인가를 고정 가격으로 생각하지 않기.** 프로모션은 끝날 수 있어요. 해상도·길이·모드·오디오를 바꿀 때마다 버튼 가격을 다시 보면 좋아요. 오디오를 끄면 항상 반값이라는 계산도 피하는 편이에요.
- **성공한 클립 하나의 총비용으로 계산.** 재시도와 마무리 비용도 함께 세면 좋아요. 낮은 해상도로 다섯 번 시험한 뒤 최종 1080p를 한 번 뽑는 예는 `5×30+160=310`, 1080p 다섯 번은 `5×160=800`이에요. 약 61% 차이지만 최종 한 번이 성공한다는 가정이며, 전용 Draft 모드의 단계별 요금 계산은 아니에요.

## 영상에 쓴 프롬프트 3개

- [1대6 골목 액션](prompts/01_action_1v6_alley.txt): 일곱 인물 유지, 타격과 반응의 순서, 빠른 카메라를 봤어요.
- [이별 클로즈업](prompts/02_drama_breakup_closeup.txt): 작은 표정 변화, 한국어 대사, 입 모양을 봤어요.
- [애니 옥상 파쿠르](prompts/03_anime_rooftop_parkour.txt): 2D 화풍 유지, 장애물 연결, 착지를 봤어요.

파일은 최종본 그대로예요. [사용 설정과 시작 이미지 안내](prompts/README.md)에 16:9·1080p·오디오·길이를 적었어요. 영상에 쓴 시작 이미지도 [prompts/frames/](prompts/frames/)에 함께 넣어 뒀어요. 프롬프트와 같이 넣으면 영상과 같은 조건으로 돌려 볼 수 있어요.

## 생성기 쓰는 법

### 1. ChatGPT·Claude·Gemini에 붙여넣기

[GENERATOR_PROMPT.md](generator/GENERATOR_PROMPT.md)를 열고 파일 전체를 새 채팅의 첫 메시지로 붙여넣으면 돼요. 시스템 지침을 넣는 칸이 있는 도구라면 그 칸에 넣어도 좋아요. 이후 장면을 한국어로 두세 줄 적어요.

```text
비 오는 밤 버스 정류장에서 여자가 친구를 기다려요.
친구를 발견하고 우산을 조금 들어 올리며 웃어요.
시작 이미지 있음, 8초, Kling 4.0. 대사는 없어요.
```

영어 프롬프트 코드 블록, 두 줄의 한국어 설명, 추천 설정을 받아요. 필요한 정보가 정말 부족할 때만 짧게 최대 두 가지를 물어요.

고칠 때는 기존 프롬프트와 `얼굴이 바뀌어요`, `동작이 느려요`, `대사가 이상해요` 같은 증상을 함께 보내면 돼요. 원래 장면을 유지하면서 수정본과 바뀐 이유를 받아요.

### 2. Claude Code / 에이전트 스킬로 설치

저장소를 다운로드한 뒤, 이 저장소 폴더에서 아래 명령으로 Claude Code의 개인 스킬 폴더에 복사할 수 있어요.

```sh
mkdir -p ~/.claude/skills/ai-video-prompt
cp skills/ai-video-prompt/SKILL.md skills/ai-video-prompt/reference.md ~/.claude/skills/ai-video-prompt/
```

설치 뒤 Claude Code에서 `/ai-video-prompt`와 장면 설명을 함께 입력하면 돼요. 이 개인 스킬 경로와 호출 방식은 [Claude Code 공식 문서](https://code.claude.com/docs/en/skills)에서도 확인할 수 있어요. 다른 에이전트는 해당 도구의 스킬 폴더에 `skills/ai-video-prompt/` 폴더 전체를 복사하면 좋아요. [스킬 본문](skills/ai-video-prompt/SKILL.md)과 [상세 규칙](skills/ai-video-prompt/reference.md)이 함께 있어야 해요.

생성기는 텍스트를 써 주는 도구예요. 실제 생성 화면에서는 길이·비율·해상도·오디오·시작 이미지 역할을 따로 맞추면 좋아요.

## 출처

아래는 조사에 참고한 54개 자료예요. 문서 정리 기준일은 2026년 10월 26일이에요. 공급사 안내는 기능 설명이며 성공률 검증은 아니고, 사용자 사례는 조건에 따라 결과가 달라질 수 있어요.

Reddit 자료는 검색에 노출된 글 기준이고 원본 영상은 별도로 검증하지 못했어요. 일부 YouTube 자료는 기존 자막 조사 또는 요약을 참고했어요. 오래된 모델 비교는 연출 참고용으로만 보면 좋아요.

### 공급사 공식 문서

- 01. [Kling 4.0 User Guide](https://kling.ai/quickstart/kling-4-model-user-guide)
- 02. [Dreamina Seedance 2.5 prompt guide](https://docs.byteplus.com/en/docs/ModelArk/seedance-2-5-prompt-guide)
- 03. [Dreamina Seedance 2.5 tutorial](https://docs.byteplus.com/en/docs/ModelArk/seedance-2-5)
- 04. [Dreamina Seedance 2.0 series prompt guide](https://docs.byteplus.com/en/docs/ModelArk/seedance-2-0-prompt-guide)
- 05. [H3 Video Prompt Writing Guide, base modes](https://huggingface.co/MiniMaxAI/MiniMax-H3/raw/main/docs/VIDEO_PROMPT_WRITING_GUIDE_base_en.md)
- 06. [MiniMax H3 repository](https://github.com/MiniMax-AI/MiniMax-H3)
- 07. [MiniMax H3: An Open Model Breaking the Boundaries Between Tasks and Modalities](https://www.minimax.io/blog/minimax-h3)
- 08. [Wan3.0 Video Generation Prompt Guide](https://www.alibabacloud.com/help/en/model-studio/wan3-video-generation-prompt-guide)
- 09. [Wan3.0 Video Generation API Reference](https://docs.modelstudio.console.alibabacloud.com/en/model-studio/wan3-video-generation-api-reference)
- 10. [How to use Wan3.0 video generation](https://www.alibabacloud.com/help/en/model-studio/wan3-video-generation-guide)
- 11. [Video Overview](https://docs.x.ai/developers/model-capabilities/video/overview)
- 12. [Image-to-Video](https://docs.x.ai/developers/model-capabilities/video/image-to-video)
- 13. [Video Generation](https://docs.x.ai/developers/model-capabilities/video/generation)
- 14. [Text-to-Video](https://docs.bfl.ai/guides/prompting_video_text_to_video)
- 15. [Audio and speech](https://docs.bfl.ai/guides/prompting_video_audio)
- 16. [Image-to-Video](https://docs.bfl.ai/guides/prompting_video_image_to_video)
- 17. [Examples & Cheatsheet](https://docs.bfl.ai/guides/prompting_video_camera_terms)
- 18. [Generate a video with FLUX 3](https://docs.bfl.ai/api-reference/utility/generate-a-video-with-flux-3)
- 19. [FLUX 3 Video, Part 1: Generation](https://bfl.ai/blog/flux-3-video)
- 20. [Generate and edit videos with Gemini Omni Flash](https://ai.google.dev/gemini-api/docs/omni)
- 22. [Gemini Omni Flash model card](https://ai.google.dev/gemini-api/docs/models/gemini-omni-flash)

### Higgsfield 안내

- 21. [Kling 4.0 on Higgsfield: Features, Settings, and Pricing](https://higgsfield.ai/blog/kling-4-0-on-higgsfield)
- 23. [Seedance 2.5 Pricing: Full Breakdown of Credits, Plans, and Cost per Clip](https://higgsfield.ai/blog/seedance-2-5-pricing-2026)
- 24. [Higgsfield Pricing Explained: Plans, Credits, and What's Included](https://higgsfield.ai/blog/higgsfield-pricing-explained)
- 25. [Pricing plans](https://higgsfield.ai/pricing)
- 26. [How do I use Seedance?](https://higgsfield.ai/creator-hub/help-center/ai-models/how-do-i-use-seedance)
- 27. [What's new in Higgsfield](https://higgsfield.ai/creator-hub/changelog)
- 28. [How do I write a good prompt?](https://higgsfield.ai/creator-hub/help-center/getting-started/how-do-i-write-a-good-prompt)
- 29. [Seedance 2.5: Complete Prompting Guide](https://higgsfield.ai/blog/seedance-2-5-prompting-guide)
- 30. [Seedance 2.5 model page](https://higgsfield.ai/seedance/2.5)
- 31. [How to Master AI Filmmaking](https://higgsfield.ai/blog/how-to-master-ai-filmmaking)
- 32. [Academy](https://higgsfield.ai/academy)
- 33. [AI Video Upscaler](https://higgsfield.ai/ai-video-upscaler)
- 34. [Generating with Seedance 2.0: Full Tutorial](https://higgsfield.ai/blog/generating-with-seedance-2-0)

### 업스케일·비교·사용 사례

- 35. [Using Topaz Labs for your Seedance 2.0 videos](https://www.topazlabs.com/learn/using-topaz-labs-for-your-seedance-videos)
- 36. [Topaz for Web Plans & Pricing / FAQ](https://docs.topazlabs.com/cloud-apps/topaz-for-web-plans-and-pricing)
- 37. [Legacy Astra Plans & Credit System / desktop Cloud Rendering](https://docs.topazlabs.com/cloud-apps/astra/plans-and-credit-system)
- 38. [[팁] 힉스필드에서 시댄스 2.5 비용 절감하는 방법](https://gall.dcinside.com/mgallery/board/view/?id=aicreate&no=67823&page=1)
- 39. [Tried FLUX 3 to upscale a Seedance 2.5 video from 480p to 1080p](https://www.reddit.com/r/FluxAI/comments/1vzmdhm/tried_flux_3_to_upscale_a_seedance_25_video_from/)
- 40. [Seedance2.5 480P to 1080P upscaling](https://www.reddit.com/r/Seedance_AI/comments/1wqvpb4/seedance25_480p_to_1080p_upscaling/)
- 41. [Does direct 1080p differ from upscaling a 480p Draft?](https://www.reddit.com/r/Seedance_AI/comments/1xdhfih/does_generating_seedance_25_directly_in_1080p/)
- 42. [Is 1080p worth it if I upscale locally from 720p?](https://www.reddit.com/r/Seedance_AI/comments/1tqjnoq/is_1080p_worth_it_if_i_upscale_locally_from_720p/)
- 43. [Seedance 2.5 fight scene: avoid slow motion](https://www.reddit.com/r/Seedance_AI/comments/1w3ts1o/seedance_25_fight_scene_avoid_slow_motion/)
- 44. [Seedance 2.0 vs Kling 3.0: AI Emotion Comparison](https://curiousrefuge.com/blog/seedance-2-vs-kling-3)
- 45. [Image-to-Video Prompting Guide](https://theailab.substack.com/p/image-to-video-prompting-guide)
- 46. [I Compared Seedance 2.5, MiniMax H3, and Wan 3](https://generativeai.pub/i-compared-seedance-2-5-minimax-h3-and-wan-3-which-ai-video-model-is-the-best-d5ff0a4508d0)
- 47. [How I Make Ultra Realistic AI Videos using Seedance 2.5](https://www.youtube.com/watch?v=Zo8KaTs0l6k)
- 48. [시댄스 2.5 일관성 미쳤다!! 달라진점 요약](https://www.youtube.com/watch?v=4ti84MYcbzE)
- 49. [Is Seedance 2.0 Mini Worth Using on Higgsfield?](https://www.youtube.com/watch?v=8ru_2B2wfb8)
- 50. [시댄스 2.5 프롬프트 작성법, AI 영상 제작 이렇게 하면 됩니다](https://m-sooriya.tistory.com/1100)
- 51. [잘 하지만 다 해주지는 못하는 AI](https://brunch.co.kr/@plusx/129)
- 52. [Best practices for generating videos](https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/video/best-practice)
- 53. [The Cinematographer and Scene Blocking, Part 2](https://sony-cinematography.com/articles/the-cinematographer-and-scene-blocking-part-2/)
- 54. [VIDEO 3.0 Omni Model User Guide](https://kling.ai/quickstart/klingai-video-3-omni-model-user-guide)
