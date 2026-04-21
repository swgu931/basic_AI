# howto setup oepncode.json

~/.opencode/opencode.json
```
{
  "$schema": "https://opencode.ai/config.json",
  "model": "ollama/gemma4:31b",
  "provider": {
    "ollama": {
      "name": "Ollama (local)",
      "options": {
        "baseURL": "http://10.232.183.148:11434/v1"
      },
      "models": {
        "qwen3.5:35b": {
          "name": "qwen3.5:35b"
        },
	"gemma4:31b": {
	  "name": "gemma4:31b"
	}
      }
    }
  }
}
```

```
$ opencode agent list
```
```
    "pattern": "/home/gusewan/.local/share/opencode/tool-output/*",
    "action": "allow"
  },
  {
    "permission": "external_directory",
    "pattern": "/home/gusewan/.agents/skills/microsoft-foundry/*",
```

```
# Custom Tools

프로젝트의 .opencode/tools/ 디렉토리(로컬)
~/.config/opencode/tools/ 디렉토리(전역)

```
