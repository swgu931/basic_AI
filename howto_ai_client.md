# howto ask to AI (Ollama exaone-deep:7.8b)


```
# GET
curl http://10.231.182.153:11434/api/version
```

```
# POST
curl http://10.231.182.153:11434/api/generate
curl http://10.231.182.153:11434/api/chat

```



```
curl http://localhost:11434/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{
    "model": "exaone-deep:7.8b",
    "messages": [{"role": "user", "content": "안녕하세요, 한국어로 대화할 수 있나요?"}]
  }'
  
  
curl http://10.231.182.153:8080/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{
    "model": "exaone-deep:7.8b",
    "messages": [{"role": "user", "content": "안녕하세요, 한국어로 대화할 수 있나요?"}],
    "temperature": 0.1
  }'
  
curl http://localhost:8080/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{
    "model": "exaone-deep:7.8b",
    "messages": [{"role": "user", "content": "안녕하세요, 한국어로 대화할 수 있나요?"}],
    "temperature": 0.1
  }'
```

