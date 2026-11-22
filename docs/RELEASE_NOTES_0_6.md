# RitaCAD 0.6 RC1 release notes

Operation EVOLVE updates the desktop modeling workspace and RitaAI. Native parts use the same analytic geometry kernel and feature history.

## Workspace

- Switch between model and sketch commands in the contextual ribbon. Use the feature tree to select and edit a feature, and switch the right panel between Properties and RitaAI.
- Choose light or dark appearance. Adjust panel widths, use the view controls, and find commands with **Ctrl+K**.
- Click a visible face to select it and double-click it to select its body. Middle-button drag pans, **Shift+middle-button drag** orbits, the wheel zooms, and **M** moves the selection.

## RitaAI

| Mode | What you can do |
| --- | --- |
| Copilot | Inspect computed dimensions and selected geometry, diagnose modeling errors, and preview a dimension change on a selected rectangle or circle sketch. |
| Teacher | Follow ten authored lessons with native document checks or guided answers. Exercises cover sketches, solids, drawing views, dimensional limits and datums. |
| Designer | Enter a supported brief, clarify missing dimensions, review the actual native preview and approve it before saving an editable part. |

Ordinary CAD and the authored workflows run without a model service. Optional local inference helps translate supported phrasing. RitaCAD checks its response against the request and uses native CAD commands to validate geometry.

## Six verified native examples

The rectangular block, block with a positioned through-hole, stepped shaft, solid L-bracket, flanged spacer and pad-and-pocket pedestal each passed the Designer geometry, dependency, save and reopen, parameter edit and undo checks.

The bracket is a sharp solid with a rectangular base and a full-width upright. The sample upright height can be edited in native feature history. A base change that invalidates its saved face reference is rejected and rolled back. Sheet-metal bends, bend radii and flat patterns are outside this release.

Teacher exercises on tolerance and datums provide educational guidance. The release verification report lists the tested configuration and remaining compatibility limits. [Operation EVOLVE verification report](EVOLVE_REPORT.md)

## Get started

Extract the [portable Windows ZIP](https://raw.githubusercontent.com/ivs-kartikeya/RitaCAD/main/downloads/v0.6-rc1/RitaCAD-v0.6-rc1-Windows-Portable.zip), open the **RitaCAD** folder and run **RitaCAD.exe**. For shortcut, setup and sample instructions, see [Getting started](GETTING_STARTED.md).
