# Known limitations — v0.5-rc2

RitaCAD is an early Windows release candidate with explicitly bounded modeling domains. Supported operations create editable native geometry; that does not imply general-purpose support for every solid or combination of features.

## Geometry and interchange

| Area | Current boundary |
| --- | --- |
| Solid composition | Rectangular face pads/pockets and other bounded operations; no general curved-solid Boolean engine |
| Prism through-bores | Up to eight separate bores on eligible convex XY prisms, including eligible translation and global-Z rotation |
| Composed pad/pocket solids | Circular drilling through these composed orthogonal solids is unsupported |
| Revolve | Full supported polygon revolves and eligible coaxial bores; no general partial revolve or off-axis drilling |
| Edge treatment | Bounded existing box operations; no arbitrary selected-edge fillets/chamfers |
| Advanced modeling | No loft, sweep, general shell/draft, spline solids, gears/threads or bent sheet-metal workflow |
| Assemblies | No assemblies or mates |
| File exchange | Native `.ritacad`, STL export and viewport images; no STEP interchange |
| Engineering analysis | No FEA, strength, fracture or manufacturing acceptance solver |

Invalid, overlapping, degenerate or out-of-domain inputs may be rejected. Use the displayed diagnostic to change the request or preserve the preceding valid model.

New multi-hole features use native schema 6. RitaCAD v0.5 reads earlier schemas 1–5; earlier releases cannot be assumed to open projects containing newer features. Keep a copy before moving between versions. STL files do not retain native sketch/feature history.

## RitaAI

- **Copilot** performs structured native inspection and offers bounded suggestions; it is not an unrestricted engineering adviser.
- **Teacher** checks eight stated exercises. It does not grade arbitrary projects, certify ASME/ISO compliance or verify manufactured parts.
- **Designer** supports bounded plate/block, spacer/shaft and pedestal recipes and a supported two-hole edit. It does not synthesize arbitrary products or assemblies.
- The optional local model passed **13/14 fixed briefs**. This is a small evaluation, and interpretation can fail. Review every proposed dimension and operation.
- The optional runtime and model require separate installation and reviewed identities. Other models and configurations are unverified.

## Verification boundaries

The application passed **416/416 software tests** in the repaired Windows development build. The public download carries the verified repaired executable. Windows GUI checks also exercised the portable application, native sample loading and Copilot. These results do not certify every user workflow or hardware configuration.

A second computer/GPU, physical DPI configurations, long-duration use and large models have not been certified. No general performance comparison with mature CAD systems is claimed.

Ordinary CAD, lessons and deterministic recipes require no model service. The optional client is restricted to loopback and the tested service reported cloud disabled. No OS-enforced internet block or whole-machine packet capture was performed; full offline acceptance remains unverified.

Save native work regularly. Recovery checkpoints do not preserve every pending click, camera change or Undo stack. Save is blocked while a Designer preview is pending; approve or cancel it first.

## Report a problem

Check whether the operation falls within this scope, then [open a bug report](https://github.com/ivs-kartikeya/RitaCAD/issues/new?template=bug_report.yml). Include the smallest reproducible steps and a non-sensitive sample if useful. Feature requests are welcome through the [feature request form](https://github.com/ivs-kartikeya/RitaCAD/issues/new?template=feature_request.yml).
