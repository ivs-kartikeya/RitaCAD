# RitaCAD 0.6 RC1 verification

Operation EVOLVE upgrades the existing Windows desktop CAD application. This release adds Model and Sketch command rows, resizable workspace panels, light and dark themes, and **Ctrl+K** command search. Sketches, constraints, feature dependencies and solid validation continue to use the native RitaCAD Geometry Kernel. Native project schemas 1–6 remain readable.

The final Windows build passed **436 tests**, up from 416 at baseline. The portable ZIP passed all 18 internal SHA-256 checks. The packaged executable verified all nine included native examples and opened the editable L-bracket in a responding Windows window from a fresh extraction under a path with spaces. The bracket regenerated one valid 28,000 mm³ body from four native features.

## RitaAI

- **Engineering Copilot** reads the current native geometry, including selected bodies, faces, edges and vertices. It can explain a recent applicable modeling failure. A supported rectangle or circle dimension can be edited through a reviewed preview, approval and Undo. The regenerated closed profile must match the requested native dimensions.
- **CAD Teacher** offers ten authored exercises covering sketching, constraints, extrusion, revolve, feature history, drawings, tolerances and introductory GD&T. It checks either native model state or bounded concept answers. Where the lesson has a geometry reference, **Locate step** can orient the workspace or select that geometry.
- **Autonomous Designer** asks for missing parameters, validates an exact feature plan in a scratch project and requires approval. Once approved, use **File → Save** for an editable `.ritacad` file. Delayed results preserve active CAD commands and stale approvals are rejected. The deterministic path works with the optional model service stopped.

## Verified models

The final executable produced six supported designs through the deterministic planner. Each passed geometry and dependency checks, was saved and reopened, and accepted a further native edit. Time covers the evaluator workflow for each case. The block ran first and includes first-use work.

| Model | Volume (mm³) | Evaluator time | Result |
| --- | ---: | ---: | --- |
| Rectangular block | 48,000.000 | 157.0 ms | Pass |
| Off-center through-hole | 47,773.805 | 19.8 ms | Pass |
| Stepped shaft | 32,986.723 | 24.2 ms | Pass |
| Solid L-bracket | 28,000.000 | 50.0 ms | Pass |
| Flanged spacer | 35,185.838 | 14.6 ms | Pass |
| Pad and pocket pedestal | 118,000.000 | 35.9 ms | Pass |

The evaluator process reached 39.3 MiB peak working set. Six targeted Teacher and Copilot scenarios passed ten repetitions each. Their warm median times ranged from under 0.01 ms to 5.37 ms in the fixture process. The Windows suite also exercises sketch cancellation and editing, native face picks, exact Join and Cut, Move, Undo and reopening/editing a saved project.

## Local model benchmark

One live local-model case used the existing Qwen 3.5 4B Q4_K_M with Ollama 0.40.13, 2,048 context tokens and four CPU inference threads. Inference was pinned to four logical processors on an Intel Core Ultra 9 275HX Windows host. The request took **24.67 seconds**, including **7.42 seconds** to load the model. The model service reported **zero model VRAM**. Peak sampled combined process working set was **3.38 GiB**, with **4.45 GiB** of private memory. The 619 prompt tokens and 29 output tokens produced a verified 100 × 60 × 8 mm plate with two native features, saved and reopened at 48,000 mm³.

During inference, a 40 ms WinForms timer recorded a 49.48 ms 95th-percentile gap and a 106.63 ms maximum gap. Synchronous viewport refresh took 14.01 ms at the 95th percentile. The host used its RTX 5060 Laptop GPU for CAD rendering. These measurements describe one tested brief on one host. Four-core 8 GB hardware, integrated-only graphics, physical multi-monitor DPI changes and system-wide network isolation remain unverified.

## Scope

The L-bracket recipe creates a sharp solid with an editable joined upright. It does not calculate sheet-metal bend allowances. Designer handles bounded recipes with explicit dimensions. General curved-solid Booleans, arbitrary blends, loft/sweep, assemblies, STEP interchange and FEA are outside the supported release scope. Classroom examples illustrate GD&T concepts. Manufacturing compliance requires independent verification.

[Getting started](GETTING_STARTED.md) · [Local AI setup](LOCAL_AI_SETUP.md) · [Known limitations](KNOWN_LIMITATIONS.md) · [Release notes](RELEASE_NOTES_0_6.md)
