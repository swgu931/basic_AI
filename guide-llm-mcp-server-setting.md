# LLM / MCP Client Comparision

![alt text](LLM_MCP-Client-Comparision.png)


# howto set on-premise llm
 
```
  vscode: (~/.config/Code/User/settings.json)   (vscode not to change llm ????)
  vscode extension : continue (~/.continue/config.yaml) 
  gemini:                                       (gemini not to change llm)
  antigravity:                                  (Antigravity not to change llm)
  ai toolkit (~/.aitk/models in case of using AI Toolkit extension of VS Code) (very limited and not operable for on-premise)
```

```bash
~/.continue$ cat config.yaml 

name: Local Config
version: 1.0.0
schema: v1
models:
  - name: GPT-4.1-nano
    provider: azure
    model: gpt-4.1-nano
    apiKey: "your key"
    apiBase: https://azureopenai-swgu.openai.azure.com/
  - name: Qwen 35B (Remote)
    provider: openai 
    model: qwen3.5:35b
    apiKey: ollama    # Put a dummy value like 'ollama' if the field is mandatory
    apiBase: http://10.231.182.153:11434/v1
```


# howto set mcp server

```
  (~/.config/Code/User/mcp.json) 
  (~/.continue/config.yaml)
  (~/.gemini/settings.json) 
  (~/.config/Antigravity/User/mcp.json)
  (~/.aitk/mcp.json in case of using AI Toolkit extension of VS Code)
```

```bash
cat ~/.config/Code/User/mcp.json 
{
	"servers": {
		"add-mcp-http": {
			"url": "http://localhost:8000/mcp",
			"type": "http"
		},
		"add-mcp-stdio": {
			"type": "stdio",
			"command": "python3",
			"args": [
				"server-stdio.py"
			]
		},
    "robo-mcp-http": {
      "url": "http://10.157.13.78:30800/sse",
			"type": "sse"
    }
  }
	"inputs": []
}

```
