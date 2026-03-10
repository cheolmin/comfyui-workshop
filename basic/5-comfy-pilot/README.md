# #5. Demos - Comfypilot

> **주의**: 이 섹션은 **선택 사항**입니다. Comfy Pilot은 Claude Code와 ComfyUI를 연결하는 고급 도구이며, 기본 워크플로우 학습에는 필수가 아닙니다.

## Comfy Pilot이란?

**Comfy Pilot**은 Claude Code와 ComfyUI를 연결하는 **MCP 서버 + 내장 터미널** 커스텀 노드입니다. ComfyUI 안에서 자연어로 워크플로우를 생성, 편집, 실행할 수 있게 해줍니다.

**핵심 기능:**

* **MCP 서버**: Claude Code가 워크플로우를 직접 조회, 편집, 실행
* **내장 터미널**: ComfyUI 안에 xterm.js 기반 Claude Code 터미널 탑재
* **이미지 뷰잉**: Claude가 Preview/Save Image 노드의 출력을 직접 확인
* **그래프 편집**: 노드 생성/삭제/이동/연결을 프로그래밍 방식으로 처리
* **모델 다운로드**: HuggingFace, CivitAI에서 모델 직접 다운로드

**사용 예시:**

* "SDXL + ControlNet 워크플로우 만들어줘"
* "프리뷰 이미지 보고 디테일 높여줘"
* "FLUX schnell 모델 다운받고 워크플로우 세팅해줘"

***

## 설치 방법

**방법 1 - CLI (권장):**

```bash
comfy node install comfy-pilot
```

**방법 2 - ComfyUI Manager:**

1. ComfyUI에서 **Manager** → **Install Custom Nodes** 클릭
2. `Comfy Pilot` 검색
3. **Install** 클릭
4. ComfyUI 재시작

**방법 3 - Git Clone:**

```bash
cd ~/Documents/ComfyUI/custom_nodes && git clone https://github.com/ConstantineB6/comfy-pilot.git
```

> Claude Code CLI가 설치되어 있지 않으면 자동으로 설치됩니다.

***

## 요구사항

* ComfyUI
* Python 3.8+

***

## 데모

아래 영상은 Comfy Pilot을 활용하여 자연어로 워크플로우를 생성하는 과정을 보여줍니다.

{% embed url="https://github.com/cheolmin/comfyui-workshop/raw/main/.gitbook/assets/comfy-pilot-demo.mp4" %}

***

## 사용 방법

1. ComfyUI 재시작 후 우측 상단에 Claude Code 터미널이 표시됨
2. MCP 서버는 자동으로 설정됨
3. Claude에게 워크플로우 관련 작업을 요청:
   * "현재 워크플로우에 어떤 노드가 있어?"
   * "체크포인트 로더에 KSampler 노드를 연결해줘"
   * "프리뷰 이미지를 보고 뭐가 보이는지 말해줘"
   * "노드 5번까지 워크플로우 실행해줘"

## MCP 도구 목록

| 도구 | 설명 |
|------|------|
| `get_workflow` | 브라우저에서 현재 워크플로우 가져오기 |
| `summarize_workflow` | 워크플로우 요약 |
| `get_node_types` | 사용 가능한 노드 타입 검색 |
| `get_node_info` | 특정 노드 타입 상세 정보 |
| `get_status` | 큐 상태, 시스템 정보, 실행 이력 |
| `run` | 워크플로우 실행 또는 중단 |
| `edit_graph` | 노드 생성, 삭제, 이동, 연결, 설정 |
| `view_image` | Preview/Save Image 노드 출력 이미지 보기 |
| `search_custom_nodes` | ComfyUI Manager 레지스트리에서 커스텀 노드 검색 |
| `install_custom_node` | 커스텀 노드 설치 |
| `download_model` | HuggingFace, CivitAI 등에서 모델 다운로드 |

***

## 아키텍처

```
┌─────────────────────────────────────────────────────┐
│  Browser (ComfyUI)                                  │
│  ┌─────────────────┐  ┌──────────────────────────┐  │
│  │  xterm.js       │  │  Workflow State          │  │
│  │  Terminal       │  │  (synced to backend)     │  │
│  └────────┬────────┘  └────────────┬─────────────┘  │
│           │ WebSocket              │ REST API       │
└───────────┼────────────────────────┼────────────────┘
            │                        │
            ▼                        ▼
┌─────────────────────────────────────────────────────┐
│  ComfyUI Server                                     │
│  ┌─────────────────┐  ┌──────────────────────────┐  │
│  │  PTY Process    │  │  Plugin Endpoints        │  │
│  │  (claude CLI)   │  │  /claude-code/*          │  │
│  └─────────────────┘  └──────────────────────────┘  │
└─────────────────────────────────────────────────────┘
            │                        │
            │                        ▼
            │           ┌──────────────────────────┐
            └──────────▶│  MCP Server              │
                        │  (stdio transport)       │
                        └──────────────────────────┘
```

***

## 트러블슈팅

| 문제 | 해결책 |
|------|-------|
| **"Command 'claude' not found"** | Claude Code CLI 설치: `curl -fsSL https://claude.ai/install.sh \| bash` |
| **MCP 서버 연결 안 됨** | ComfyUI 콘솔에서 에러 확인. `~/.claude.json`에 MCP 설정 수동 추가 |
| **터미널 연결 끊김** | 터미널의 ↻ 버튼 클릭하여 재연결 |

***

## Amazon Bedrock으로 사용하기

이 워크샵에서는 AWS 환경에서 운영하므로, Claude Code를 Anthropic API 대신 **Amazon Bedrock**을 통해 사용할 수 있습니다.

### 환경변수 설정

ComfyUI를 시작하기 전에 다음 환경변수를 설정합니다.

```bash
export CLAUDE_CODE_USE_BEDROCK=1
export AWS_REGION=us-west-2
```

SageMaker 환경에서는 IAM Role을 통해 AWS 자격증명이 자동으로 제공되므로 별도의 Access Key 설정이 필요 없습니다.

특정 프로필을 사용해야 하는 경우:

```bash
export AWS_PROFILE=your-profile-name
```

### 필요한 IAM 권한

Bedrock을 통해 Claude를 호출하려면 IAM Role에 다음 권한이 필요합니다.

```json
{
    "Effect": "Allow",
    "Action": [
        "bedrock:InvokeModel",
        "bedrock:InvokeModelWithResponseStream"
    ],
    "Resource": "arn:aws:bedrock:*::foundation-model/anthropic.*"
}
```

### 확인 방법

환경변수 설정 후 ComfyUI를 재시작하면, Comfy Pilot 내장 터미널에서 실행되는 Claude Code가 자동으로 Bedrock을 통해 호출됩니다. MCP 서버 쪽은 별도 수정이 필요 없습니다.

***

## 참조

* GitHub 레포지토리: https://github.com/ConstantineB6/comfy-pilot
* ComfyUI Registry: https://registry.comfy.org/publishers/constantine/nodes/comfy-pilot
* Claude Code with Bedrock: https://docs.anthropic.com/en/docs/claude-code/bedrock-vertex
* 라이선스: MIT
