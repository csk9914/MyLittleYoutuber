<div align="center">
  <h1>My Little Youtuber · 나작유</h1>
  <p>하루의 행동을 계획해 나만의 유튜버를 키우는 육성 시뮬레이션</p>
  <p>
    <a href="https://youtu.be/q5gqqgeEDjw">구현 포트폴리오</a> ·
    <a href="https://youtu.be/AJXVIvXP3EU">게임 트레일러</a> ·
    <a href="https://github.com/csk9914/MyLittleYoutuber">GitHub 저장소</a>
  </p>
  <a href="https://youtu.be/q5gqqgeEDjw">
    <img src="https://img.youtube.com/vi/q5gqqgeEDjw/hqdefault.jpg" alt="My Little Youtuber 구현 포트폴리오 영상" width="640">
  </a>
</div>

## 프로젝트 개요

방송으로 영상을 만들고, 편집과 업로드로 수익과 구독자를 늘려가는 유튜버 육성 시뮬레이션입니다. 하루를 행동 단위로 운영하며 D+365의 구독자 수에 따라 엔딩이 결정됩니다.

| 항목 | 내용 |
|---|---|
| 개발 기간 | 2022.03 – 2022.06 |
| 팀 구성 | 4명 (기획 1명, 프로그래밍 3명) |
| 엔진 / 언어 | Unity 2020.3 / C# |
| 담당 | 게임 시스템 · UI 프레임워크 |
| 저장소 | [csk9914/MyLittleYoutuber](https://github.com/csk9914/MyLittleYoutuber) |

## 담당 범위와 기여

게임의 공통 시스템과 UI 기반을 설계하고, 방송·영상 파트의 팀원 시스템이 연결될 수 있도록 데이터 흐름과 인터페이스를 구현했습니다.

| Plastic SCM 이력 기준 | 기여 |
|---|---:|
| 전체 261개 커밋 중 담당 커밋 | 144개 (55%) |
| 직접 작성한 스크립트 | 116개 |
| 팀원 담당 파일에 반영한 통합·버그 수정 | 41개 파일 |
| `DatabaseManager` 수정 | 34개 변경 |

### 주요 구현

- **확장 가능한 상점 프레임워크** — 콘텐츠, 가구, 편집자 고용, FLEX 상점을 공통 `BaseUI`와 목록·정렬 팩토리 조합으로 통합했습니다. 기존 enum/switch 분기를 컴포넌트 조립 방식으로 바꿔 새 상점을 추가할 때 변경 지점을 줄였습니다.
- **행동 상태머신** — 휴식·수면·방송·편집·미용·운동을 `IState` 기반 상태로 분리했습니다. 날짜, D-day, 소모품, 주급과 엔딩 처리는 `GlobalState`로 나눴습니다.
- **공통 UI 프레임워크** — `PopupBuilder`로 구매·확인·완료 팝업 생성 경로를 통일하고, Observer 기반 갱신으로 HUD와 상점 목록이 데이터 변경을 반영하도록 구성했습니다.
- **데이터와 저장 구조** — 기획 값은 프리팹 데이터로 관리하고, 플레이 진행은 CSV로 저장했습니다. `DatabaseManager`, `GameSceneManager`, `AudioManager` 등 공용 매니저도 구현했습니다.
- **팀 시스템 연동** — 플레이어가 편집자로 영상 파이프라인에 참여하도록 연결하고, 뉴스 태그 변경 시 콘텐츠 인기도를 다시 계산해 시청자와 수익 시스템에 전달했습니다.
- **플레이 편의 기능** — DOTween 페이드와 비동기 씬 로딩, BGM/SE 및 볼륨 저장, 한글 닉네임 검증, 세로 화면 해상도 대응을 구현했습니다.

### 설계 회고

- 문자열 이름과 `GameObject.Find`에 의존한 상태 탐색은 enum과 캐시된 상태 맵으로 바꾸고, 상태 전환 규칙을 `StateMachine` 한 곳에서 검증하는 편이 낫습니다.
- 여러 책임이 모인 `GlobalState`와 `DatabaseManager`는 날짜 변경 이벤트와 데이터 기능 단위로 나누면 수정 범위를 줄일 수 있습니다.

## 실행

1. 저장소를 Unity Hub에 추가하고 Unity 2020.3으로 엽니다.
2. `Assets/01.Scenes/TitleScene.unity`를 열어 Play합니다.

아트와 사운드는 팀 그래픽 파트의 창작물이며, 저장소는 학습 및 포트폴리오 목적으로 공개되어 있습니다.

