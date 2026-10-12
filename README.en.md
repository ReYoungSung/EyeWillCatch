[한국어](README.md) | **English**

# EyeWillCatch

A research game for eye rehabilitation exercises using webcam-based gaze tracking. It was developed for research involving patients with post-stroke diplopia and is associated with KCGS 2023, the Korea Computer Graphics Society conference.

## Background

The project connects external gaze-to-mouse software to a Unity game. Several game ideas were used to explore gaze input. Webcam tracking accuracy was affected by factors such as the user's face and position.

## Team

CGLab (Computer Graphics Laboratory) — 이영성 (Youngsung Ree), 이용석, 김현진

## Development environment

| Item | Value |
| --- | --- |
| Unity Editor | **2021.3.21f1** |
| Unity project folder | `KCGs/` |
| Default branch | `main` |

The Unity version is taken from [ProjectVersion.txt](KCGs/ProjectSettings/ProjectVersion.txt).

- Webcam
- External software that converts gaze tracking to mouse movement (the original development setup used tools such as GazeRecorder's GazePointer)

## Getting started

```bash
git clone --branch main https://github.com/ReYoungSung/EyeWillCatch.git
```

1. Install the Editor version above through Unity Hub.
2. Add the repository's `KCGs` folder as a project. The repository root and Unity project folder are different.
3. Complete the initial import and Package Manager dependency restoration.
4. Open a scene as described below and enter Play mode.

Open one of `Game1Scene.unity`, `Game2FollowScene.unity`, `Game6Scene.unity`, or `UI Scene.unity` in `Assets/Scenes/`. The scene list in `EditorBuildSettings.asset` is empty, so there is no configured entry scene. Before creating a build, add the required scenes to Build Settings in the intended order.

See [EditorBuildSettings.asset](KCGs/ProjectSettings/EditorBuildSettings.asset) for build configuration and [manifest.json](KCGs/Packages/manifest.json) for dependencies. The `Assets/` paths below are relative to the Unity project folder.

## Main folders

| Path | Contents |
| --- | --- |
| [Assets/Scenes/](KCGs/Assets/Scenes/) | Game and UI scenes |
| [Assets/Scripts/](KCGs/Assets/Scripts/) | Game1, Game2, Game6, timer, and scoring logic |

## Checking input

1. Calibrate the external gaze tracker and verify that the mouse cursor follows your gaze.
2. Run the selected Unity scene and check input and UI responses.
3. If the cursor is misaligned, first check camera/face positioning and calibration in the external software.

## Usage

### Preparation and scene selection

1. Start the webcam and gaze-to-mouse software, then finish calibration.
2. Verify that changing your gaze moves the operating system's mouse cursor.
3. Open the game scene you want to try in Unity and enter Play mode. Since no default entry scene is configured, test the games individually.
4. Look at the targets and check whether the character, light, or ray follows your gaze position. Before connecting gaze tracking, use a mouse to check input responses.

| Scene | Controls and progression |
| --- | --- |
| `Game1Scene.unity` | Move the cursor toward appearing thieves to move the police character. Contact with the detection area increases the score. A score screen appears after the configured number of appearances. |
| `Game2FollowScene.unity` | The light rotates toward the cursor position. Follow the on-screen targets with your gaze. |
| `Game6Scene.unity` | Point at a thief with the cursor to hit it with the ray. Detection is based on ray hits and does not require clicking. |

The light may move even when the cursor is not visible: Game2's light script hides the cursor during play.

### Ending and switching scenes

Exit Play mode to end the current experience in the Editor. Game1's ending code transitions to `Game2Scene`, while the scene file listed above is named `Game2FollowScene`. To enable continuous play, align the transition names with the Build Settings entries. Until then, run each scene independently.

Behavior references: [MouseCharacter.cs](KCGs/Assets/Scripts/Game1/MouseCharacter.cs) · [GameController.cs](KCGs/Assets/Scripts/Game1/GameController.cs) · [MoveLight.cs](KCGs/Assets/Scripts/Game2/MoveLight.cs) · [MouseRay.cs](KCGs/Assets/Scripts/Game6/MouseRay.cs)
