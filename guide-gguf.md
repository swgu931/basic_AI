
# Convert EXAONE to ollam gguf format
# https://github.com/LG-AI-EXAONE/EXAONE-Deep



```
pip install huggingface_hub
```

<!-- huggingface-cli download LGAI-EXAONE/EXAONE-Deep-7.8B-GGUF \
    --include "EXAONE-Deep-7.8B-BF16*.gguf" \
    --local-dir . -->
    
```    
huggingface-cli download LGAI-EXAONE/EXAONE-Deep-2.4B-GGUF \
    --include "EXAONE-Deep-2.4B-BF16*.gguf" \
    --local-dir .
```        

## chat LLM
```
llama-cli -m ./EXAONE-Deep-2.4B-BF16.gguf \
    -sys "" \
    -c 32768 \
    --temp 0.6 \
    --top-p 0.95 \
    --jinja \
    --chat-template "{% for message in messages %}{% if loop.first and message['role'] != 'system' %}{{ '[|system|][|endofturn|]\n' }}{% endif %}{% set content = message['content'] %}{% if '</thought>' in content %}{% set content = content.split('</thought>')[-1].lstrip('\\n') %}{% endif %}{{ '[|' + message['role'] + '|]' + content }}{% if not message['role'] == 'user' %}{{ '[|endofturn|]' }}{% endif %}{% if not loop.last %}{{ '\n' }}{% endif %}{% endfor %}{% if add_generation_prompt %}{{ '\n[|assistant|]<thought>\n' }}{% endif %}"    
```    
    
## Write the Modelfile for EXAONE Deep.    
```
# Model path (choose appropriate GGUF weights on your own)
FROM ./EXAONE-Deep-7.8B-BF16.gguf

# Parameter values
PARAMETER stop "[|endofturn|]"
PARAMETER repeat_penalty 1.0
PARAMETER num_ctx 32768
PARAMETER temperature 0.6
PARAMETER top_p 0.95

# Chat template
#   Note: currently there is no feature of removing `<thought></thought>` steps from context 
#   because ollama does not support yet. We will update when according feature is available.
TEMPLATE """{{- range $i, $_ := .Messages }}
{{- $last := eq (len (slice $.Messages $i)) 1 -}}
{{ if eq .Role "system" }}[|system|]{{ .Content }}[|endofturn|]
{{ continue }}
{{ else if eq .Role "user" }}[|user|]{{ .Content }}
{{ else if eq .Role "assistant" }}[|assistant|]{{ .Content }}[|endofturn|]
{{ end }}
{{- if and (ne .Role "assistant") $last }}[|assistant|]<thought>
{{ end }}
{{- end -}}"""

# System prompt
SYSTEM """"""

# License
LICENSE """EXAONE AI Model License Agreement 1.1 - NC """
```    


## Convert the model to Ollama
```
ollama create EXAONE-Deep-2.4B-BF16 -f Modelfile
```


## Check list
```
ollama list
```

## Run the model with Ollama.
```
ollama run exaone
```


# convert 사용

```bash
# Huggingface 나 기타 모델 저장소에서 GGWF 파일을 다운로드함

ollama convert <model path> --outtype gguf --verbose /path/to/output/gguf/file
```


