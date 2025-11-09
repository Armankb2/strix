## Fix: TOOL Server Connectivity Issue (#74)

This document explains how to resolve Docker and LLM connection issues in the Strix project.

### 🧩 Root Cause
Strix CLI threw the following errors:
- 'Docker not available'
- 'LLM connection failed'

This happened because:
- Docker daemon was not running
- Missing local LLM API base configuration
- Ollama not installed or model not loaded

### 🛠 Steps to Resolve
1. Install Docker Desktop or Colima:
   ```bash
   brew install docker colima
   colima start
   ```

2. Install Ollama and pull the Llama3 model:
   ```bash
   brew install ollama
   ollama pull llama3
   ```

3. Export the required environment variables:
   ```bash
   export STRIX_LLM='ollama/llama3'
   export LLM_API_BASE='http://localhost:11434'
   ```

4. Run the Strix agent:
   ```bash
   poetry run strix --target https://github.com/usestrix/strix.git
   ```

### ✅ Result
- Docker daemon successfully connected  
- LLM model initialized (Llama3 via Ollama)  
- StrixAgent executed the penetration test without errors

### 💡 Verified On
- macOS 15.6.1 (Apple M2)
- Poetry 2.2.1
- Docker 28.5.1
- Ollama 0.12.10

### 👤 Contributor
Contributed by [@Armankb2](https://github.com/Armankb2)

