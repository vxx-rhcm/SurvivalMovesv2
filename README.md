# SurvivalMoves — GitHub Actions build

This repository builds `SurvivalMoves.dll` as a **.NET Framework 4.8 Class Library** on a Windows GitHub Actions runner.

## Required dependency

Add the matching `ScriptHookVDotNet3.dll` reference assembly to:

```text
lib/ScriptHookVDotNet3.dll
```

Use the reference DLL from the ScriptHookVDotNet (SHVDN3) release/version intended for the GTA V installation. Do not use `LemonUI.SHVDN3.dll` or `NativeUI.dll` as a replacement; they are different libraries.

The dependency is intentionally not bundled. It is an external runtime/reference component and should be obtained from its official project/release. If you do not want to commit the DLL to a public repository, keep the repository private or modify the workflow to retrieve a pinned official release asset.

## Build on GitHub

1. Create a GitHub repository and upload all files from this folder.
2. Add `lib/ScriptHookVDotNet3.dll` as described above.
3. Push to `main` or `master`, or open **Actions → Build SurvivalMoves → Run workflow**.
4. Open the completed workflow run.
5. Under **Artifacts**, download `SurvivalMoves-net48`.
6. Extract `SurvivalMoves.dll` and install it in GTA V's `scripts` folder. Remove/backup older copies first to avoid duplicate scripts.

## Build settings

- Runner: `windows-latest`
- Build tool: MSBuild
- Configuration: `Release`
- Platform: `AnyCPU`
- Target framework: `.NET Framework 4.8`
- Output: `bin/Release/SurvivalMoves.dll`
- Artifact: `SurvivalMoves-net48`

## Notes

- GitHub Actions only compiles the source; it cannot verify in-game behavior.
- The game and ScriptHookV/ScriptHookVDotNet must be compatible with the chosen dependency version.
- The red-circled touch controls in the supplied screenshot are provided by the game/host touch overlay, not created by this script. Disable them in the host's touch-control configuration.
