# Optional local inference

The installed model used for testing was `qwen3.5:4b` Q4_K_M with Ollama 0.40.13. Get Ollama from its official Windows distribution and review the model license and exact identity before installing weights.

[Ollama for Windows](https://ollama.com/download/windows) · [Ollama local configuration](https://docs.ollama.com/faq) · [Qwen model license](https://huggingface.co/Qwen/Qwen3.5-4B/blob/main/LICENSE)

If a reviewed compatible model is already installed, a separate PowerShell session can start a loopback service on a free port. The settings apply to the child service process.

```powershell
$env:OLLAMA_HOST = '127.0.0.1:11435'
$env:OLLAMA_NO_CLOUD = '1'
$env:OLLAMA_NUM_PARALLEL = '1'
$env:OLLAMA_MAX_LOADED_MODELS = '1'
$env:OLLAMA_KEEP_ALIVE = '30s'
ollama serve
```

In RitaAI open **Designer → Local model settings**. Set `http://127.0.0.1:11435`, the installed reviewed model name, and its exact SHA-256 model digest. The pinned Qwen digest for this build is `d8b0f5e9760cd1682034f292d7ef72ec46f432149be0df7574bf2d6e92e38c04`. **Check local model connection** verifies readiness before loading weights. **CPU only** offers a four-thread preset with 2048 context tokens. The compute cost depends on the host and request.

Ordinary CAD, the authored lessons and supported deterministic plans work with the service stopped. Runtime and model weights are separate from the portable ZIP. Only literal loopback endpoints, a cloud-disabled service and a matching reviewed model identity are accepted. Report the displayed readiness status when asking for help.
