# LLaMa manual


```bash
https://github.com/ollama/ollama
```

# Ollama install
```bash
curl -fsSL https://ollama.com/install.sh | sh
```


```bash

ollama pull llama3.2:1b

ollama run llama3.2:1b
```



## how to make my own customized model for the llama3.2:1b through Customizing a prompt
```bash

vi Modelfile
---
FROM llama3.2:1b

# set the temperature to 1 [higher is more creative, lower is more coherent]
PARAMETER temperature 1

# set the system message
SYSTEM """
You are Mario from Super Mario Bros. Answer as Mario, the assistant, only.
"""
---





vi Modelfile
---
FROM /home/aistation/workspace-llm/llm_server/llm_models/models--LGAI-EXAONE--EXAONE-4.0-32B-GGUF/snapshots/b390c77d8be64849356ff7bc6213c8049b5a34b2/EXAONE-4.0-32B-Q4_K_M.gguf
# 필요한 경우 파라미터나 시스템 프롬프트를 추가할 수 있습니다. 
PARAMETER num_ctx 4096
PARAMETER temperature 0.7
---
ollama create exaone-4.0-32b-ollama -f ./Modelfile
ollama list




ollama create llama3.2:1b-mario -f ./Modelfile
ollama run llama3.2:1b-mario

ollama rm llama3.2:1b-mario
ollama cp llama3.2:1b-mario my-model

ollama show
ollama list
ollama ps
ollama stop llama3.2

# Start Ollama
ollama serve # : is used when you want to start ollama without running the desktop application.

# Multiline input
# For multiline input, you can wrap text with """:
---
>>> """Hello,
... world!
... """
I'm a basic program that prints the famous "Hello, world!" message to the console.
---

```

## Multimodal models
```bash
ollama run llama "What's in this image? /Users/jmorgan/Desktop/smile.png"
```

## Pass the prompt as an argument
```bash
ollama run llama3.2 "Summarize this file: $(cat README.md)"
```

# REST API

## Generate a response
```bash
curl http://localhost:11434/api/generate -d '{
  "model": "llama3.2",
  "prompt":"Why is the sky blue?"
}'
```


## Chat with a model
```bash
curl http://localhost:11434/api/chat -d '{
  "model": "llama3.2",
  "messages": [
    { "role": "user", "content": "why is the sky blue?" }
  ]
}'
```


## howto check the LLM support Embedding model
```bash

curl http://localhost:11434/api/embeddings \
-d '{"model": "EXAONE-Deep-2.4B-BF16", "prompt": "임베딩할 문장"}'

curl http://localhost:11434/api/embeddings \
-d '{"model": "llama3.2:1b", "prompt": "임베딩할 문장"}'

```

## Model Library


![alt text](<Screenshot from 2025-03-24 13-55-26.png>)

