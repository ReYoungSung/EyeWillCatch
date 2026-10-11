# EyeWillCatch

웹캠 기반 시선 추적 입력을 활용한 눈 재활운동 연구용 게임입니다. 뇌졸중 후 복시 환자를 대상으로 한 연구를 위해 제작했으며, 한국컴퓨터그래픽스학회 KCGS 2023 관련 프로젝트입니다.

## 프로젝트 배경

시선을 마우스 커서로 변환하는 외부 소프트웨어와 Unity 게임을 연결했습니다. 다양한 게임 아이디어로 시선 추적 입력을 실험했으며, 웹캠의 인식 정확도가 사용자의 얼굴·위치 등 환경에 영향을 받는 한계가 있었습니다.

## 팀

CGLab(컴퓨터그래픽스 연구실) — 이영성, 이용석, 김현진

## 개발 환경

| 항목 | 값 |
| --- | --- |
| Unity Editor | **2021.3.21f1** |
| Unity 프로젝트 폴더 | `KCGs/` |
| 기본 브랜치 | `main` |

Unity 버전은 [ProjectVersion.txt](KCGs/ProjectSettings/ProjectVersion.txt)에 기록된 값을 기준으로 합니다.

- 웹캠
- 시선 추적 결과를 마우스 커서로 변환하는 외부 소프트웨어(기존 개발 환경 예: GazeRecorder의 GazePointer)

## 시작하기

```bash
git clone --branch main https://github.com/ReYoungSung/EyeWillCatch.git
```

1. Unity Hub에 위 버전의 Editor를 설치합니다.
2. 저장소 안의 `KCGs` 폴더를 프로젝트로 추가합니다. 저장소 최상위 폴더와 Unity 프로젝트 폴더는 서로 다릅니다.
3. 최초 임포트와 Package Manager의 패키지 복원을 완료합니다.
4. 아래 씬 안내에 따라 확인할 씬을 열고 Play를 실행합니다.

`Assets/Scenes/`의 `Game1Scene.unity`, `Game2FollowScene.unity`, `Game6Scene.unity`, `UI Scene.unity` 중 확인할 씬을 직접 엽니다. `EditorBuildSettings.asset`의 씬 목록이 비어 있어 기본 시작 씬은 지정되어 있지 않습니다. 실행 파일을 만들려면 필요한 씬과 순서를 Build Settings에 먼저 등록해야 합니다.

빌드 구성은 [EditorBuildSettings.asset](KCGs/ProjectSettings/EditorBuildSettings.asset), 패키지 목록은 [manifest.json](KCGs/Packages/manifest.json)에서 확인할 수 있습니다. 아래 `Assets/` 경로는 Unity 프로젝트 폴더 기준입니다.

## 주요 폴더

| 경로 | 내용 |
| --- | --- |
| [Assets/Scenes/](KCGs/Assets/Scenes/) | 게임 및 UI 씬 |
| [Assets/Scripts/](KCGs/Assets/Scripts/) | Game1·Game2·Game6, 타이머·점수 로직 |

## 입력 확인

1. 외부 시선 추적 프로그램에서 보정을 완료하고 마우스 커서가 시선을 따라 움직이는지 확인합니다.
2. Unity에서 선택한 씬을 실행해 입력과 UI 반응을 확인합니다.
3. 커서 위치가 어긋나면 카메라·얼굴 위치와 외부 프로그램의 보정 상태를 먼저 점검합니다.
