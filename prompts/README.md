# 영상에 쓴 프롬프트

[한국어 가이드](../README.md) · [English guide](../README.en.md)

Asle's Workroom의 「AI 영상 모델 8개, 같은 프롬프트로 싹 다 비교」에 쓴 최종 영어 프롬프트예요. 파일 전체를 복사하면 됩니다. 세 파일은 영상용 최종본 그대로라, 입문용 생성기 예시보다 동작과 카메라 지시가 촘촘해요.

| 파일 | 장면에서 살펴본 것 | 길이 |
|---|---|---:|
| [01_action_1v6_alley.txt](01_action_1v6_alley.txt) | 밤 골목 1대6 액션: 인원 유지, 타격 접촉, 반응 순서, 빠른 카메라 | 8초 |
| [02_drama_breakup_closeup.txt](02_drama_breakup_closeup.txt) | 이별 클로즈업: 작은 표정 변화, 한국어 한 문장, 입 모양 | 10초 |
| [03_anime_rooftop_parkour.txt](03_anime_rooftop_parkour.txt) | 옥상 파쿠르: 2D 화풍 유지, 장애물 연결, 착지, 추적 카메라 | 10초 |

## 사용 설정

16:9 · 1080p · 오디오 켜기 · 시작 프레임을 넣는 이미지→영상(I2V) 방식이에요. 오디오 스위치가 있는 화면에서는 켜고, 없는 화면에서는 모델의 기본 오디오를 사용했어요. 길이는 액션 8초, 드라마·애니 10초예요.

이는 비교 영상의 공통 설정 기준이에요. 모델·등급마다 해상도 메뉴가 다를 수 있어요. 예를 들어 MiniMax H3 Standard는 가격표에서 2K로 구분했어요. 프롬프트에 쓴 길이와 실제 생성 화면의 설정도 함께 맞추면 좋아요.

## 시작 프레임

영상에 쓴 시작 이미지는 [frames/](frames/)에 있어요. 프롬프트와 파일 이름이 같아요(1920×1080 JPG).

| 장면 | 시작 이미지 |
|---|---|
| 액션 | [01_action_1v6_alley.jpg](frames/01_action_1v6_alley.jpg) |
| 드라마 | [02_drama_breakup_closeup.jpg](frames/02_drama_breakup_closeup.jpg) |
| 애니 | [03_anime_rooftop_parkour.jpg](frames/03_anime_rooftop_parkour.jpg) |

세 프롬프트 모두 시작 이미지의 인물·옷·위치를 전제로 해서, 이미지 없이 텍스트만 넣으면 결과가 많이 달라져요.

다른 이미지를 쓰면 그 이미지에 맞게 인물 구분과 동선을 바꾸면 좋아요. 애니 장면은 시작 이미지도 같은 2D 애니 화풍으로 준비하면 좋아요.

## English

These are unchanged final prompts from the comparison video. Shared setup: 16:9, 1080p target, audio on, image-to-video using a start frame; action 8s, drama and anime 10s. Where no audio toggle exists, use native audio. Resolution availability varies by model/variant; H3 Standard is listed separately at 2K in the price table.

The start frames used in the video are in [frames/](frames/), named like their prompts (1920×1080 JPG). Text alone does not reproduce the comparison conditions. Match wardrobe, positions and route to your own image; use an already-drawn anime image for the anime scene.
