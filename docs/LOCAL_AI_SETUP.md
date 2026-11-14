# Optional local language model

Normal CAD, native demo editing, the eight guided lessons, computed Copilot inspection and supported deterministic Designer recipes run without a model. Enable the optional model only when you want help translating other supported wording into design intent.

## Reviewed configuration

The v0.5 release candidate was tested with Ollama **0.40.13** and **qwen3.5:4b**, Q4_K_M quantization, on an RTX 5060 Laptop GPU with 8 GB VRAM. The reviewed model digest is:

```text
d8b0f5e9760cd1682034f292d7ef72ec46f432149be0df7574bf2d6e92e38c04
```

Ollama and model weights are separate installations, not included in RitaCAD. Review the [official Ollama distribution](https://ollama.com/download/windows) and [Qwen model license](https://huggingface.co/Qwen/Qwen3.5-4B/blob/main/LICENSE) before installing or downloading anything. RitaCAD never downloads weights. A current model tag may resolve to different weights; an identity mismatch is rejected rather than silently substituted.

## Run an existing reviewed installation

If you already have the reviewed local model installed, open a separate PowerShell window and start a headless service using process-local settings:

```powershell
$env:OLLAMA_HOST = '127.0.0.1:11435'
$env:OLLAMA_NO_CLOUD = '1'
$env:OLLAMA_CONTEXT_LENGTH = '4096'
$env:OLLAMA_NUM_PARALLEL = '1'
$env:OLLAMA_MAX_LOADED_MODELS = '1'
$env:OLLAMA_KEEP_ALIVE = '30s'
ollama serve
```

Leave that window open while using the model. Ctrl+C stops this service. These commands do not persist machine/user environment settings. Use a separate unused loopback port; do not interrupt another service or change firewall rules. If the model is absent, install a reviewed local model yourself using the runtime's official instructions. RitaCAD has no automatic model-download action.

In RitaCAD choose **RitaAI → Open local AI workspace → Autonomous Designer**. Under Local model settings use endpoint `http://127.0.0.1:11435`, model `qwen3.5:4b` and the exact reviewed digest. Save settings; they persist per user. Choose **Check local model connection** to verify metadata/identity without loading weights. Tick **Use local model for design intent** only when needed. Complete simple briefs use deterministic rules; missing mandatory dimensions and unsupported geometry do not start inference. A model cannot invent dimensions.

The CPU-only option sends zero model GPU layers and exposes a bounded thread/context/output/deadline profile. The preset uses four threads and a 2048 context. On the tested runtime a requested 1024 context was clamped to 2048. The diagnostic CPU/UI request took 17.7 seconds and sampled about 4.45 GiB private commit across CAD/client/runtime processes. This is not an 8 GB quad-core/integrated-GPU certification; see the diagnostic report before selecting hardware.

The client requires a literal loopback address, explicit cloud-disabled status and the reviewed local model identity. It rejects redirects, cloud-enabled or stopped services, truncated/malformed output and timeouts. No remote fallback is used. Model output becomes bounded intent data and still passes native CAD validation. Inspect the preview before approving any change.

## Measured results and limits

The repaired fixed local-model evaluation passed **13 of 14** cases. The remaining failure misclassified an existing-hole edit as a new plate and was rejected. The six valid/design-edit cases scored 5/6. This is a small fixed evaluation, not evidence of general CAD autonomy. Complete supported hole edits normally use deterministic rules instead of calling the model.

The recorded cold request took about 5.1 seconds including model loading; warm requests took 0.51–0.96 seconds. An earlier resource sample peaked at about 5.3 GB total GPU use including the desktop, with about 1.16 GiB combined sampled model/client process working set. Different hardware and workloads can differ.

The client only contacts loopback and the tested service had cloud features disabled. Process-scoped negative-proxy and sampled-traffic checks were performed. An OS-enforced internet-isolated acceptance test and whole-machine packet capture were **not** performed. Local inference is an architectural boundary, not a claim that all other software on your computer is offline.
