# RitaAI diagnostic, repair and optimization audit

14 November 2026 · RitaCAD v0.5 AI repair candidate (v0.5-rc2)

**Outcome:** focused repairs pass **416/416 application regressions**. The 13-case deterministic/adversarial Designer diagnostic improves from **3/13 to 13/13**. A fresh forced local-model evaluation passes **13/14**, compared with the earlier 12/14 release evaluation. This remains a bounded parametric CAD assistant, not an unrestricted conversational engineering agent. No replacement model was downloaded; the proprietary kernel was unchanged.

## Architecture actually present

`LocalModelClient` calls only a literal loopback Ollama endpoint. It verifies cloud-disabled status, exact local tag/digest and local completion capability, then requests bounded JSON. `CadDesigner` recognizes bounded recipes; a model reply must preserve source-bound dimensions and operations. `CadToolEngine` builds an isolated native document, regenerates/validates it and requires approval before one undoable commit. The authoritative result is editable native sketch/feature history, not display triangles.

Teacher is eight authored lessons with fixed state-derived exercises. Copilot is deterministic native inspection; this repair adds bounded read-only questions. Neither mode currently calls a language model. Their content and routing are hardcoded application logic. That is useful for predictable lessons/facts, but does not implement general tutoring or engineering conversation. Designer is a bounded recipe compiler with an optional confirmatory language translator. There is no general agent search, conversation memory, long-term personalization, retrieval index, assembly reasoning or self-learning loop.

Document awareness comes from isolated native snapshots, actual feature parameters, regenerated bodies and solver diagnostics. Copilot can reject stale cached results. The model receives a bounded textual context, not unrestricted file or kernel access. There is no model shell/source execution or arbitrary filesystem tool.

## Confirmed defects and repairs

| Finding and owning source | Reproduction / root cause | Repair and evidence |
| --- | --- | --- |
| Supported native shapes unreachable: `ai/CadDesigner.cs` | Block wording, one off-center hole and a solid stepped shaft failed before native execution. Independent preauthored plans worked on the original kernel. | Added bounded aliases, a single-hole variant and a solid-shaft recipe using existing tools. Native volume, occupancy, history, reopen/re-edit/Undo regressions. |
| Wrong dimension extraction: `ai/CadDesigner.cs` | Conflicting labels chose the first value; base depth was stolen from pocket cut depth; malformed `100,5` could become 100 or 5; attached mm/exponents failed. | Conservative token boundaries, label-role binding and conflict detection. Ambiguity clarifies instead of truncating a value. |
| Ungrounded model acceptance: `ai/CadDesigner.cs` | Explicit slab dimensions could be swapped; unrelated reference numbers could authorize invented holes; requested extra features could disappear. | Independently compile role-bound source intent and require an identical native plan. Unknown hole counts, blind/through contradictions and unsupported additions reject safely. |
| False Teacher completion: `ai/CadEducation.cs` | A frozen boundary passed using unrelated construction dimensions, or redundant dimensions that could not actually resize it. The old test only found matching values and zero DOF. | Isolated finite dimension-edit probes verify that width/depth controls change the target rectangle. Both false positives now fail; original valid lessons still pass. |
| Wasteful inference: `ui/RitaAiWorkflow.cs` | Any non-ready result, including missing dimensions and unsupported geometry, started HTTP/model work if the checkbox was enabled. | `CanUseLocalModel` gates supported, fully grounded paraphrases. Known rejections and essential clarifications make **zero HTTP requests**. UI identifies deterministic versus model paths. |
| Restart/setup opacity: `ui/RitaAiWorkflow.cs`, `ai/LocalModelSettings.cs` | Endpoint/model choices lived only in the form; reopening lost them. No metadata-only readiness control existed. | Atomic, validated per-user settings with corrupt-data warnings; explicit connection check reports endpoint/reason without loading weights. Tests cover new-window restoration, invalid save retention and corrupt/duplicate settings. |
| Ambiguous transport JSON: `ai/LocalModelClient.cs`, `ai/CadToolEngine.cs` | Duplicate cloud/completion keys were silently overwritten by the serializer. | Strict bounded duplicate-key/JSON validation precedes deserialization. Contradictory cloud status and completion fixtures reject. Safety guards remain enabled. |
| Copilot interaction gap: `ai/CadCopilot.cs`, `ui/RitaAiWorkflow.cs` | The named Copilot had only an inspection report and no question entry. | Added `Ask` for current volume/bounds/dimensions, constraints and supported-operation failures. Hypothetical strength/geometry questions do not masquerade as computed results. Supported edits route to the reviewed Designer pipeline. |
| Public debug metadata: `build.ps1`, `RitaCAD.csproj` | Release executable contained a private developer PDB path despite not bundling the PDB. | Default release compilation disables debug symbols. Developers can explicitly request private debug symbols. Public distributions exclude source/scripts/debug output. |

Before-fix logs are retained locally, including configuration 0/3, transport 0/2, UI inference-gating 0/1 and the authored Teacher counterexamples. A first integration run was 414/1: its old delayed-model fixture used wording deliberately excluded by the new gate. The fixture now uses a supported complete slab paraphrase and still proves that an actual delayed reply cannot overwrite a dirty sketch. Final full suite: **416 passed, 0 failed**. Earlier sandbox socket denials and a private harness sample-path failure were environmental failures, not relabeled AI successes.

## Progressive Designer tests

| Request | Executed result | Failure classification |
| --- | --- | --- |
| Rectangular block, 100×60×8 mm | Native sketch + extrusion, 48,000 mm³; save/reopen/edit/Undo verified | Repaired intent coverage; kernel already capable |
| Same plate with one Ø6 through-hole at (25,20) | One valid native bored solid, 48,000−72π mm³, correct empty hole center and retained material | Repaired single-hole recipe; kernel already capable |
| Solid stepped shaft, Ø20×80 total, Ø30×20 flange | Editable XZ profile + full revolve, 10,500π mm³; solid axis, no invented bore | Repaired shaft/spacer distinction; kernel already capable |
| Bent mounting bracket | Explicit unsupported result; no box substitute or hidden mutation | No bounded bend/bracket planner is implemented. This does not imply that every sharp orthogonal bracket shape is impossible manually. |
| 100×80×8 base + 60×50×20 pad + 30×20×10 pocket | Six native features with durable supports, one valid 118,000 mm³ solid | Existing bounded multi-feature workflow passes |

Native evidence also checks stable IDs, independent volume/occupancy, unchanged source state, save/reopen and continued parameter edits. These tests do not establish arbitrary mechanical product generation.

## Teacher and Copilot tests

The original ten education/inspection cases plus nine new mode cases pass. Tests include true controlling dimensions, incomplete/wrong GD&T answers, transformed geometry in centimetres, exact bounds and volume, conflicting constraints, invalid heights with stale cached bodies, missing selection and unsupported drilling through a pad/pocket cell solid. Copilot reports the actual kernel restriction for that last case; it does not blame model connectivity.

Actual Windows UI verification entered “What is the volume?” into Copilot and received the correct 130952.21 mm³ visible-volume result for the example part, explicitly labelled rule-based. Designer's new connection check showed LOCAL SERVICE READY for the reviewed loopback model without generating or changing CAD. Both observations were captured and the application closed normally.

Sketching, constraints, extrusion/revolve, native history and introductory datum/location-control concepts are taught through authored exercises. General engineering-design tutoring, arbitrary question answering, PMI/tolerance solving and ASME/ISO compliance remain absent. The public references are original lesson background, not copied/paywalled standards text. Previewed hole editing works; arbitrary conversational feature editing is not implemented.

## Runtime and local-model evidence

The existing reviewed installation is Ollama **0.40.13**, **qwen3.5:4b Q4_K_M**, approximately 3.32 GB model data, pinned digest `d8b0f5e9760cd1682034f292d7ef72ec46f432149be0df7574bf2d6e92e38c04`. The existing cloud-disabled service was reachable on 127.0.0.1:11435. No reproducible model load crash or transport disconnect occurred during these bounded tests. One should not infer a crash diagnosis from an incorrect intent or an unsupported geometry request.

The fresh 14-brief GPU evaluation scored **13/14**. The remaining failure returned a new-plate intent for an existing-hole edit, including an illegal field; the host rejected it. Normal application routing handles that complete edit deterministically without calling the model. This improvement is a small fixed-set result, not statistical proof of broad accuracy or a claim that every model failure is repaired.

The transport retains cloud/digest/loopback/redirect guards, one finite deadline and cancellation. No retry loop, paid service, cloud fallback or model download is used. Metadata checks occur before generation; their local overhead was not the dominant latency. The default 30-second keep-alive can unload idle weights, adding cold-load latency. Longer keep-alive trades RAM for latency and was not silently imposed. No memory leak was demonstrated by the short samples; they also cannot rule out long-duration leaks.

## CPU-only and low-end investigation

Actual host: **Core Ultra 9 275HX, 24 physical/logical processors, about 15.38 GiB RAM, RTX 5060 Laptop GPU**. This is not the target student laptop. CPU inference was explicitly forced with `num_gpu=0`, four threads and affinity mask 0xF on owned server/runner/client processes. Runtime logs showed the CPU backend, `/api/ps` reported zero model VRAM, and temporary servers were cleaned. A four-logical-processor affinity is a simulation, not an older physical quad-core benchmark.

| Measurement | Actual observation |
| --- | --- |
| Headless service ready/startup | 1.423–4.330 seconds in the three owned-server runs; separate from loading model weights |
| CPU baseline, nine bounded calls | Approximately 14.5–17.4 seconds; about 8.85–9.84 generated tokens/s |
| GPU comparison, three calls | Cold 4.019 seconds; warm 0.576–0.797 seconds; about 85–88 generated tokens/s |
| Requested CPU context 1024 | Runtime clamped it to **2048**; it was not a smaller effective allocation |
| CPU 4096 versus 2048 | About 66–67 MiB higher sampled private commit; weights/runtime dominate memory |
| Final actual production-client CPU/UI call | 17.743 seconds, 547 prompt tokens, 29 output tokens; about 3.608 seconds model load and 3.141 seconds output evaluation |
| Final native result | Correct slab→plate intent, one valid 48,000 mm³ native preview; source and visible CAD documents unchanged |
| Final sampled CAD/client/server/runner memory | Peak working set **3.66 GiB**, private commit **4.45 GiB**; these are different metrics |
| CPU inference model VRAM | **0** |
| GPU model allocation in comparison | About **2.86 GiB** reported model VRAM; driver/desktop totals differ |
| UI heartbeat while CPU inference ran | 40 ms timer; p95 gap 56.81 ms, maximum 67.44 ms, 372 inference ticks |
| Forced OpenGL viewport refresh | p95 10.02 ms, maximum 52.70 ms; zero renderer diagnostics |

The final UI test used actual `MainForm`, the production `LocalModelClient`, strict reply validation and native preview generation. OpenGL still used the **RTX 5060**, so integrated-GPU responsiveness remains unverified. Timer/forced-refresh timings are not mouse-input latency or certified viewport FPS.

**8 GB feasibility is unverified and tight.** No real 8 GB machine, VM or system RAM cap was used. Roughly 4.45 GiB process private commit leaves limited room for Windows, CAD and other applications; commit is not identical to resident physical RAM. The host already had other memory consumers. No swapping-free startup or acceptable latency on an older quad-core/integrated GPU can be promised. Runtime CPU logs disabled mmap by default; forcing it requires a separate controlled experiment, not an assumed optimization.

The client only contacts loopback and the tested headless services reported cloud disabled. No OS-enforced whole-machine internet block or packet capture was performed. No replacement weights, runtime installation, global environment setting, firewall change or unrelated process termination occurred.

## Recommended next architecture and model requirements

1. Keep native CAD tools/transactions authoritative. Expand domain coverage only with independently verified shape, history and rollback fixtures.
2. Route every host-resolved request directly to deterministic tools. The current strict grounding can already resolve some model-bound paraphrases, so those calls remain partly confirmatory and can be consolidated later.
3. Separate constrained intent extraction, schema/semantic validation and grounded explanation. Use compact task-specific schemas and small selected-feature context; keep authored teacher content separate from model claims.
4. Add explicit session memory only with bounded, document-versioned facts and stale-state checks. Do not feed an unbounded transcript or treat old/generated dimensions as authorization.
5. For student hardware, evaluate a reviewed roughly **1–2B, 4-bit** instruction model with reliable short JSON extraction, no required thinking trace, 2048 effective context and 128–384 output tokens. Require a permissive/reviewed license, exact digest, proven CPU operation and measured total memory/latency. These are evaluation requirements, not a recommendation to download untested replacement weights now.
6. Establish acceptance on a genuine 8 GB quad-core integrated-GPU laptop, including cold filesystem cache, idle and loaded CAD viewport, background applications, an approved offline environment and a longer resource soak. Profile selective native regeneration before adding concurrency complexity.

## Reproduction and publication

Build: `build.ps1` (release symbols disabled); full suite: `run-tests.ps1`. Relevant cases are in `RitaAiDiagnosticDesignerTests.cs`, `RitaAiDiagnosticModeTests.cs`, `RitaAiConfigurationTests.cs`, and the existing local-model/UI safety suites. Runtime measurements are repeatable with `run-ai-diagnostics.ps1`; `-Mode Cpu -Contexts '2048' -Ui` uses an owned local service and actual UI/client. Existing reviewed weights are required; the script does not download them.

Private raw evidence remains under `work/ai-diagnostic-*` and selected retained regression logs. Public publication contains this sanitized report, compact numeric evidence, user documentation, native examples and a clean compiled download. **Application/kernel source and regression-test source remain private**, following the user's explicit choice. The public downloads repository is `https://github.com/ivs-kartikeya/RitaCAD`; it has separate history from the private source repository. No source remote was present at audit start, so no private code is force-pushed or exposed there.
