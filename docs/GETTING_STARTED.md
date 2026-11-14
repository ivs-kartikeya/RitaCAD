# Getting started with RitaCAD

## Download and launch

1. Download **RitaCAD-v0.5-Windows-Portable.zip** from the [v0.5-rc2 release](https://github.com/ivs-kartikeya/RitaCAD/releases/tag/v0.5-rc2).
2. Right-click the ZIP and choose **Extract All**.
3. Open the extracted folder, then double-click **RitaCAD.exe**.

Keep the extracted folder together when moving it. Launching from inside the compressed ZIP can leave required files unavailable. You do not need Visual Studio or other build tools.

The application requires **Windows x64, Microsoft .NET Framework 4.8 and working OpenGL support**. The .NET runtime is not bundled. If Windows specifically requests it, install .NET Framework 4.8 from Microsoft and reopen RitaCAD. This executable does not run on macOS, Linux, Android or iOS.

The release page includes SHA-256 checksums. To calculate the downloaded file's hash in PowerShell, run this in the folder containing it and compare the result with the release checksum:

```powershell
Get-FileHash -Algorithm SHA256 .\RitaCAD-v0.5-Windows-Portable.zip
```

## Open your first native project

Choose **File > Open** and browse to **samples/v05** inside the extracted folder.

| Example | What to inspect |
| --- | --- |
| `mounting-plate-2holes.ritacad` | A 100 × 60 × 8 mm plate with two Ø6 mm through-bores |
| `stepped-spacer.ritacad` | A revolved Ø30 mm body, Ø50 × 8 mm flange, 40 mm total length and Ø10 mm bore |
| `pedestal-pad-pocket.ritacad` | A base with a rectangular face pad and a pocket |

**Feature History** is on the left, the **viewport** is in the middle and **Properties** is on the right. Select a feature to inspect its parameters. To edit a sketch, select its history entry and choose **Edit selected**, or double-click its tree row. Change a controlling dimension, then choose **Finish sketch** to regenerate dependent features.

Use **File > Save** to write a native `.ritacad` project to a writable folder. Keep a separate copy of a sample before experimenting. Native projects preserve editable history; an STL export contains triangles and is not a replacement for the native file.

## Navigate the viewport

| Action | Control |
| --- | --- |
| Select a visible face | Left click |
| Select the face's body | Double left click |
| Pan | Middle mouse drag |
| Orbit | Shift + middle mouse drag |
| Zoom | Mouse wheel |
| Fit all | **F** in model mode |
| Fit selection | **Shift+F** outside text entry |
| Standard views | Upper-right view control |

In sketch mode, **F** fits and realigns the active sketch. Finish or cancel an active sketch before starting another modeling operation.

## Try the local assistant

Open **RitaAI > Open local AI workspace**, or press **Ctrl+Shift+A**.

- Choose **Engineering Copilot**, then **Ask / inspect document**, for computed model facts.
- Choose **CAD Teacher** for a lesson, hint and **Check my work**.
- Choose **Autonomous Designer** to build a supported part from a complete brief and review its preview.

These workflows work without a language model. Read the [RitaAI guide](RITAAI.md) for examples and optional local-model requirements.

## If something goes wrong

First confirm that you extracted the entire ZIP and that `RitaCAD.exe` is present. If Windows or RitaCAD displays an error, keep its full message for a bug report. For display problems, include your GPU and driver version if known.

Read [known limitations](KNOWN_LIMITATIONS.md), then [report a reproducible bug](https://github.com/ivs-kartikeya/RitaCAD/issues/new?template=bug_report.yml). Include your Windows version, RitaCAD version and exact steps. Review screenshots and logs for personal information before posting them publicly.
