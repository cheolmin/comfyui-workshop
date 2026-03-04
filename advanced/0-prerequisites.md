## 사전 준비 사항

1. `..\ComfyUI_windows_portable\ComfyUI\user\__manager`의 `config.ini` 파일의 `security_level = weak`로 수정해주세요.
2. 가능하다면 **Civitai API Key**와 **HuggingFace API Key**를 사전에 발급받으실 수 있게 공지 부탁드립니다.

### 사전 설치 필요 커스텀 노드

아래 커스텀 노드들은 매니저로 설치가 어려워 **배포 전 설치 상태로 배포**되어야 합니다.

| 커스텀 노드 | 링크 | 비고 |
|---|---|---|
| ComfyUI-Yedp-Action-Director | https://github.com/yedp123/ComfyUI-Yedp-Action-Director | 스켈레톤이 있는 FBX 파일 필요 (`ComfyUI\input\yedp_anims` 경로) |
| comfyui-GaussianViewer | https://github.com/CarlMarkswx/comfyui-GaussianViewer | 오류 시 `pip install numpy, torch, Pillow` |
| ComfyUI-Qwen-TTS | https://github.com/flybirdxx/ComfyUI-Qwen-TTS | requirements 설치 및 transformers 특정 버전 필요 |

**ComfyUI-Qwen-TTS 설치 커맨드:**
```bash
python_embeded\python.exe -m pip install -U "transformers==4.57.3" "tokenizers<0.20" --no-cache-dir
python_embeded\python.exe -m pip install -r ComfyUI\custom_nodes\ComfyUI-QwenTTS\requirements.txt --no-cache-dir
```