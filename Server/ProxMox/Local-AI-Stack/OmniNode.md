# <h2 align="center">Installation Report — Local AI Stack (Open WebUI + Ollama)</h2>

![webUI](https://github.com/Juliocesar-sec/Enterprise-Home-Lab/blob/b516d978f28bfa2842d55d48e531bae4141b6b63/Local-AI-Stack/ScreenShot/iaa.png)

## Environment

- Host: Debian
- Virtualization: Oracle VirtualBox
- VM: Ubuntu Server
- Docker: installed
- Ollama: version 0.24.0
- Model used: `qwen3:8b`
- Frontend: Open WebUI

---

## Topology

```text
Debian Host
└── VirtualBox
    └── Ubuntu Server
        └── Docker
            └── Ollama
                └── qwen3:8b
```

---

## Objective

Create a local ChatGPT-style web interface using:

- Ollama
- Open WebUI
- Docker
- Free local models

---

## Final Structure

```text
Browser
    ↓
Open WebUI (port 8080)
    ↓
Ollama (port 11434)
    ↓
Local model (qwen3:8b)
```

---

## Docker Installation

Verification:

```bash
docker version
```

Result:

```text
Docker version 29.5.2
```

---

## Ollama Installation

Command:

```bash
curl -fsSL https://ollama.com | sh
```

Verification:

```bash
ollama --version
```

Result:

```text
ollama version 0.24.0
```

---

## Starting the Ollama Service

```bash
sudo systemctl enable ollama
sudo systemctl start ollama
```

Check status:

```bash
systemctl status ollama
```

Expected result:

```text
active (running)
```

---

## Ollama Test

```bash
curl http://127.0.0.1:11434
```

Expected response:

```text
Ollama is running
```

---

## Downloading the Model

Installed model:

```bash
ollama pull qwen3:8b
```

Verify:

```bash
ollama list
```

Expected result:

```text
qwen3:8b
```

---

## Open WebUI Installation

Functional container:

```bash
docker run -d \
  --network=host \
  --name open-webui \
  -e OLLAMA_BASE_URL=http://127.0.0.1:11434 \
  -v open-webui:/app/backend/data \
  --restart unless-stopped \
  ghcr.io/open-webui/open-webui:main
```

---

## Web Access

Open in the browser:

```text
http://VM_IP:8080
```

Example:

```text
http://192.168.0.187:8080
```

---

## Troubleshooting

### 1. Docker Permission

Error:

```text
permission denied while trying to connect to the Docker API
```

Solution:

```bash
sudo usermod -aG docker $USER
newgrp docker
```

### 2. Model Not Appearing

Error:

```text
Model not selected
```

Cause:

- Open WebUI could not access Ollama

Incorrect configuration:

```text
http://docker.internal
```

Correct configuration:

```text
http://127.0.0.1:11434
```

### 3. Error 500

Cause:

- Container created without correct communication with Ollama

Solution:

- Recreate using:

```bash
--network=host
```

---

## Final Functional Configuration

### Ollama

```bash
ollama serve
```

or:

```bash
sudo systemctl start ollama
```

### Open WebUI

```bash
docker run -d \
  --network=host \
  --name open-webui \
  -e OLLAMA_BASE_URL=http://127.0.0.1:11434 \
  -v open-webui:/app/backend/data \
  --restart unless-stopped \
  ghcr.io/open-webui/open-webui:main
```

---

## Recommended Models

### Fastest

```bash
ollama pull llama3.2:3b
```

### Best Balance

```bash
ollama pull qwen3:8b
```

### Best for Code

```bash
ollama pull qwen2.5-coder:14b
```

### Best Reasoning

```bash
ollama pull deepseek-r1:14b
```

---

## Performance Issues & Recommendations

### Root Cause of Slowness
The system experienced latency due to:
- Running on a VM
- No GPU acceleration
- 8B model size constraints
- CPU-only execution
- Nested virtualization overhead

### Optimization Steps

#### Increase VM RAM
- **8 GB** minimum
- **16 GB** ideal

#### Increase CPUs
In VirtualBox settings: `Settings → System → Processor`
- **4 vCPUs** minimum

#### Lighter Models
Best option for strict CPU environments:
```bash
ollama pull llama3.2:3b
```

---

## Available Features

- ChatGPT-style interface
- Local models
- No paid API
- Multi-user support
- Chat history
- Local network access

---

## Future Improvements

- HTTPS implementation
- Tailscale remote access
- Cloudflare Tunnel integration
- Dedicated NVIDIA GPU passthrough
- RAG (Retrieval-Augmented Generation) with PDFs
- Google Auth Login integration
- Nginx Reverse proxy

---

## Final Status

- ✅ Docker working
- ✅ Ollama working
- ✅ Open WebUI working
- ✅ Local model installed
- ✅ Browser access configured
- ✅ Environment operational
