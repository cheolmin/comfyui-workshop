# ComfyUI Workshop

ComfyUI는 생성형 AI를 위한 노드 기반 인터페이스 및 추론 엔진입니다.

사용자는 노드를 통해 다양한 AI 모델과 작업을 결합하여 더 높은 수준의 맞춤형 및 제어 가능한 생성 파이프라인을 구현할 수 있습니다.

이번 워크샵에서는 AWS 환경에서 ComfyUI를 프로비저닝하고, 다양한 생성형 AI 워크플로우를 직접 구성하고 실습합니다.

---

## 대상 및 사전 준비사항

**이 워크샵은 다음과 같은 분들에게 적합합니다**:
- AI 이미지/비디오 생성에 관심이 있는 초보자
- Stable Diffusion을 처음 접해보는 분
- ComfyUI를 체계적으로 배우고 싶은 분
- AWS에서 생성형 AI를 활용하고 싶은 개발자

**사전 준비사항**:
- AWS 계정 (워크샵용)
- Chrome 또는 Firefox 브라우저
- 기본적인 컴퓨터 조작 능력
- 프로그래밍 지식 불필요
- AI/머신러닝 배경 지식 불필요

---

## 0. Setup

| 순서 | 주제 | 내용 | 소요 시간 |
|------|------|------|----------|
| 0-0 | [Prerequisites](0.-setup/0-prerequisites.md) | ComfyUI 개념, 용어 정리, 사전 설정 | 15분 |
| 0-1 | [Setup](0.-setup/1-setup.md) | ECS 기반 ComfyUI 설치 및 설정 | 15분 |

---

## 1. Basic Workshop

Stable Diffusion의 기본 개념부터 다양한 이미지/비디오 생성 워크플로우까지 단계별로 실습합니다.

| 순서 | 주제 | 내용 | 소요 시간 |
|------|------|------|----------|
| 1-1 | [Workflow 알아보기](basic/2-workflow-basics/) | Stable Diffusion 워크플로우 구성 및 실습 | 40분 |
| | [Text-to-Image](basic/2-workflow-basics/2-1-text-to-image.md) | 텍스트에서 이미지 생성 | |
| | [Image-to-Image](basic/2-workflow-basics/2-2-image-to-image.md) | 이미지 기반 이미지 생성 | |
| 1-2 | [LoRA 실습](basic/3-lora/) | SDXL LoRA 적용 및 Stacking | 30분 |
| 1-3 | [워크플로우 실습](basic/4-workflow-practices/) | 다양한 워크플로우 실습 | 120분 |
| | [ControlNet](basic/4-workflow-practices/4-1-controlnet.md) | 구도 제어 | 20분 |
| | [Upscaler](basic/4-workflow-practices/4-2-upscaler.md) | CCSR / SUPIR 업스케일러 | 15분 |
| | [Z-Image](basic/4-workflow-practices/4-3-z-image.md) | Z-Image Turbo 이미지 생성 | 15분 |
| | [Qwen Image](basic/4-workflow-practices/4-4-qwen-image.md) | Qwen Image Edit / Layered | 15분 |
| | [Image Relighting](basic/4-workflow-practices/4-5-image-relighting.md) | LBM 기반 Relighting | 15분 |
| | [Wan 2.2](basic/4-workflow-practices/4-6-wan22.md) | Wan 2.2 비디오 생성 (Optional) | 20분 |
| | [Wan 2.2 LoRA](basic/4-workflow-practices/4-7-wan22-lora.md) | Wan 2.2 LoRA 활용 (Optional) | 20분 |
| 1-4 | [Comfy-pilot](basic/5-comfy-pilot/) | (Optional) Comfy-pilot 데모 | 10분 |

**추천 학습 순서**:
1. 0번 Setup과 1-1, 1-2는 순서대로 진행 (필수)
2. 1-3 워크플로우 실습은 관심사에 따라 선택적으로 진행
   - 이미지 생성: ControlNet, Upscaler, Z-Image
   - 이미지 편집: Qwen Image, Image Relighting
   - 비디오 생성: Wan 2.2, Wan 2.2 LoRA

---

## 2. Advanced Workshop

3D, 비디오, 오디오 등 고급 생성형 AI 워크플로우를 다룹니다.

> Advanced 워크샵은 별도의 사전 준비가 필요합니다. [Prerequisites](advanced/0-prerequisites.md)를 먼저 확인하세요.

| 순서 | 주제 | 내용 |
|------|------|------|
| 2-0 | [Prerequisites](advanced/0-prerequisites.md) | Advanced 사전 준비사항 |
| 2-1 | [Yedp Action Director](advanced/1-yedp-action-director.md) | 3D 애니메이션 데이터 기반 ControlNet 패스 렌더링 |
| 2-2 | [VNCCS Pose Studio](advanced/2-vnccs-pose-studio.md) | 인물 포즈 제어 및 카메라/라이팅 세팅 |
| 2-3 | [3DGS 씬 재생성](advanced/3-3dgs.md) | 단일 이미지에서 3D Gaussian Splatting 씬 생성 |
| 2-4-1 | [Image 2 Video (LTX2)](advanced/4-1-ltx-video.md) | LTX2 모델 기반 Image-to-Video |
| 2-4-2 | [Audio + Text 2 Video](advanced/4-2-qwen-tts-ltx-2.md) | Qwen TTS + LTX2 멀티모달 비디오 생성 |

---

## 워크샵 진행 흐름도

```
[0. Setup]
    Prerequisites → 환경 구축
         ↓
[1. Basic Workshop]
    Workflow 알아보기 → LoRA 실습 → 워크플로우 실습
    ├─ ControlNet (구도 제어)
    ├─ Upscaler (해상도 향상)
    ├─ Z-Image (빠른 생성)
    ├─ Qwen Image (이미지 편집)
    ├─ Image Relighting (조명 조정)
    ├─ Wan 2.2 (비디오 생성)
    └─ Wan 2.2 LoRA (비디오 스타일링)
         ↓
[2. Advanced Workshop]
    ├─ Yedp Action Director (3D 애니메이션)
    ├─ VNCCS Pose Studio (포즈 제어)
    ├─ 3DGS (3D 씬 생성)
    └─ LTX2 비디오 (멀티모달 생성)
```

---

## AWS 환경에서 ComfyUI를 활용하는 장점

1. **유연한 배포 옵션**
   * 단일 EC2부터 컨테이너화 된 ECS/EKS까지 요구사항에 맞게 선택 가능
   * 다양한 컴퓨팅 리소스를 워크로드에 맞춰 활용 가능 (CPU only / GPU)
   * Spot Instance 활용으로 비용 절감 가능
2. **사용량 기반 비용**
   * 필요할 때만 리소스를 사용하고 비용 지불
3. **운영 및 관리**
   * 통합 환경에서 중앙화 된 운영 및 모니터링 가능
   * IaC 기반 자동화 된 배포
4. **보안**
   * IAM 기반 접근 제어 및 Cognito, SAML 인증 통합
   * 네트워크 분리
   * IP 및 도메인 제한, WAF를 이용한 애플리케이션 보호

## AWS Samples

* [ComfyUI on ECS](https://github.com/cheolmin/cost-effective-aws-deployment-of-comfyui)
* [ComfyUI on EKS](https://github.com/aws-samples/comfyui-on-eks)
* [ComfyUI on SageMaker](https://github.com/aws-samples/comfyui-on-amazon-sagemaker)
