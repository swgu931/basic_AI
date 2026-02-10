# Ollama install
curl -fsSL https://ollama.com/install.sh | sh


# Ollama serve in case of systemctl

sudo systemctl edit ollama.service

```
ini
[Service]
Environment="OLLAMA_HOST=0.0.0.0"
```

sudo systemctl stop ollama
sudo systemctl daemon-reload
sudo systemctl restart ollama

ollama stop exaone-deep:7.8b
ollama run exaone-deep:7.8b



# Ollama serve in case of serve command


export OLLAMA_HOST=0.0.0.0:11434
export OLLAMA_ORIGINS="*"
ollama run exaone-deep:7.8b


~/.config/ollama/config.yml 파일에 다음을 추가:
host: "0.0.0.0"
port: 11434



# Diagnosis


포트 점유 프로세스 확인
```
sudo lsof -i :11434
또는

BASH

sudo netstat -tulnp | grep 11434
```


## Network check

curl http://localhost:11434/api/version
curl http://10.231.182.153:11434/api/version

sudo ufw status
sudo ufw allow 11434/tcp
sudo ufw status



# ollama serve --help
```
Environment Variables:
      OLLAMA_DEBUG               Show additional debug information (e.g. OLLAMA_DEBUG=1)
      OLLAMA_HOST                IP Address for the ollama server (default 127.0.0.1:11434)
      OLLAMA_CONTEXT_LENGTH      Context length to use unless otherwise specified (default: 4k/32k/256k based on VRAM)
      OLLAMA_KEEP_ALIVE          The duration that models stay loaded in memory (default "5m")
      OLLAMA_MAX_LOADED_MODELS   Maximum number of loaded models per GPU
      OLLAMA_MAX_QUEUE           Maximum number of queued requests
      OLLAMA_MODELS              The path to the models directory
      OLLAMA_NUM_PARALLEL        Maximum number of parallel requests
      OLLAMA_NOPRUNE             Do not prune model blobs on startup
      OLLAMA_ORIGINS             A comma separated list of allowed origins
      OLLAMA_SCHED_SPREAD        Always schedule model across all GPUs
      OLLAMA_FLASH_ATTENTION     Enabled flash attention
      OLLAMA_KV_CACHE_TYPE       Quantization type for the K/V cache (default: f16)
      OLLAMA_LLM_LIBRARY         Set LLM library to bypass autodetection
      OLLAMA_GPU_OVERHEAD        Reserve a portion of VRAM per GPU (bytes)
      OLLAMA_LOAD_TIMEOUT        How long to allow model loads to stall before giving up (default "5m")
```
```
ollama.service 만 실행 중인고, 내가 ollama run을 안했는데도 추론 모델이 실행이 되고 있는데 이유가 뭐야?

ollama.service가 실행 중일 때 ollama run을 하지 않았음에도 모델이 로드되어 추론이 진행되는 이유는 Ollama의 서버 아키텍처와 자동 로딩 메커니즘 때문입니다. 주요 이유는 다음과 같습니다. 
1. API 호출에 의한 자동 로딩
Ollama는 서버형 애플리케이션으로, 외부에서 API 요청(예: POST /api/generate 또는 POST /api/chat)이 들어오면 해당 요청에 지정된 모델을 즉시 메모리에 로드하여 추론을 시작합니다. 
만약 Open WebUI, 호스트 앱, 혹은 특정 스크립트가 백그라운드에서 Ollama 서버(11434 포트)에 요청을 보내고 있다면, 사용자가 터미널에서 직접 명령어를 치지 않아도 모델은 실행됩니다.

2. 'Keep Alive' 메커니즘
모델은 한 번 로드되면 추론이 끝난 직후 바로 종료되지 않습니다. 
기본 유지 시간: Ollama는 효율성을 위해 마지막 요청 이후 기본적으로 5분 동안 모델을 메모리에 유지(Keep-alive)합니다.
이 시간 동안은 추가적인 로딩 시간 없이 즉각적인 응답이 가능하므로, 사용자가 보기에 모델이 계속 "실행 중"인 것처럼 보일 수 있습니다. 

3. 이전 세션의 잔류
이전에 ollama run으로 모델을 사용했다가 터미널만 닫았을 경우, 서버 프로세스(ollama serve)는 여전히 백그라운드(systemctl 서비스)에서 돌고 있기 때문에 모델이 메모리에 남아 있을 수 있습니다. 
```

