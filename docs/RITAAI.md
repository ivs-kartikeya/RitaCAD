# RitaAI in v0.5

Open **RitaAI > Open local AI workspace**, or press **Ctrl+Shift+A**. **Back to properties** returns to ordinary editing. CAD, the eight lessons, computed inspection and supported deterministic design recipes work without a model service.

## Engineering Copilot

Choose **Engineering Copilot > Ask / inspect document**. RitaCAD regenerates an isolated copy of the native model and reports dimensions, bounds, volume, dependencies and sketch diagnostics. Select a feature first to inspect its parameters. Suggestions are identified separately from measured facts.

Copilot does not calculate strength, FEA results, manufacturing acceptance or standards compliance.

## CAD Teacher

Choose a lesson, read the exercise and hint, and use the ordinary CAD controls. **Check my work** checks native geometry, constraints and feature relationships against the lesson's stated objectives. A matching feature is selected when available; a similar feature name alone cannot pass a lesson.

The eight exercises cover a constrained rectangle, constrained circle, extrusion, face pad, pocket, revolved spacer, native re-edit/roundtrip and introductory datum/location-control concepts. Exercises use millimetres.

The edit/reopen check validates an isolated native roundtrip and further edit; it does not observe the sequence of your disk saves. The datum/GD&T exercise uses structured answers and introduces concepts. It does not implement PMI, tolerance solving, inspection or ASME/ISO compliance certification.

## Autonomous Designer

Start with a complete brief. These three families create real editable native sketches and features:

```text
mounting plate width 120 depth 80 thickness 6 hole diameter 8 hole x1 30 hole x2 90 hole y 40 mm

stepped spacer outer diameter 30 inner diameter 10 length 40 flange diameter 50 flange length 8 mm

pedestal width 100 depth 80 thickness 8 pad width 60 pad depth 50 pad height 20 pocket width 30 pocket depth 20 pocket height 10 mm
```

1. Finish or cancel any active sketch draft.
2. Enter a brief and choose **Build reviewed preview**.
3. Inspect the preview solid and exact feature plan. The current project stays unchanged.
4. Choose **Approve as new native part**, or cancel. The usual unsaved-project check still applies.
5. Use **File > Save** to save an editable `.ritacad` project. One Undo reverses the approved batch.

For an eligible two-hole project, tick **Edit current project**, then try:

```text
make both holes diameter 10 and move outward 5 mm
```

Review the result and choose **Approve changes to current part**. Invalid overlaps, unsupported geometry and stale previews are rejected. **Cancel** or **Esc** leaves the current project unchanged. Saving is blocked while a preview is pending.

Missing required dimensions receive a clarification; unsupported requests are rejected. Designer covers these bounded recipes and edits, rather than arbitrary parts, machines or assemblies.

## Optional local language model

Simple supported briefs use deterministic rules. **Use local model for design intent** opts into a separately installed local runtime for other wording. The tested setup used **Ollama 0.40.13 with `qwen3.5:4b` Q4_K_M**. Neither runtime nor weights are bundled. RitaCAD does not install them, start a server automatically or fall back to a cloud model.

The client requires a cloud-disabled service at a literal loopback address, a reviewed local model tag and its exact digest. Saved model settings must match that service. Follow the [optional local-model setup guide](LOCAL_AI_SETUP.md) before enabling it; a missing or stopped service leaves ordinary CAD available.

Model replies supply constrained intent data. RitaCAD validates supplied dimensions, supported operations and resulting native geometry before showing a preview. The model cannot execute code, launch processes, open URLs, choose arbitrary file paths or directly change the active document.

The repaired evaluation passed **13/14 fixed briefs**. The remaining failure misclassified an existing-hole edit as a new plate and was rejected. Complete supported edits use deterministic rules in the normal application. This small fixed set is not proof of general CAD reliability.

The client is restricted to loopback, and no non-loopback flow was observed for the tested processes. An **OS-enforced internet-blocked acceptance run was not performed**. This is not whole-machine offline certification.
