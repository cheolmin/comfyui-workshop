# #2-4-1. Image 2 Video (LTX2)

**LTX2 모델**은 비디오 + 오디오를 한 번에 생성하는 멀티모달 모델입니다. 오디오와 비디오가 같은 시간축을 공유하며, 이 둘을 함께 모달리티로 취급하는 점에서 현 시점 다른 오픈 웨이트 비디오 모델과 차별점이 있습니다.

이 워크플로는 기본에 충실한 LTX2 Image-to-Video 워크플로입니다.

## 모델 다운로드

Model Manager에서 다음 모델을 다운로드합니다:

| 모델                                                                | 다운로드 링크                                                                                  |                                                                           |
| ----------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| LTX-2-Image2Vid-Adapter.safetensors                               | https://huggingface.co/MachineDelusions/LTX-2\_Image2Video\_Adapter\_LoRa                | <img src="../.gitbook/assets/image (7).png" alt="" data-size="original">  |
| ltx-2-19b-ic-lora-detailer.safetensors                            | https://huggingface.co/Lightricks/LTX-2-19b-IC-LoRA-Detailer                             | <img src="../.gitbook/assets/image (8).png" alt="" data-size="original">  |
| ltx-2.3-22b-distilled\_transformer\_only\_fp8\_scaled.safetensors | [https://huggingface.co/Kijai/LTX2.3\_comfy ](https://huggingface.co/Kijai/LTX2.3_comfy) | <img src="../.gitbook/assets/image (9).png" alt="" data-size="original">  |
| LTX23\_audio\_vae\_bf16.safetensors                               | [https://huggingface.co/Kijai/LTX2.3\_comfy ](https://huggingface.co/Kijai/LTX2.3_comfy) | <img src="../.gitbook/assets/image (11).png" alt="" data-size="original"> |
| tx-2.3\_text\_projection\_bf16.safetensors                        | [https://huggingface.co/Kijai/LTX2.3\_comfy ](https://huggingface.co/Kijai/LTX2.3_comfy) | <img src="../.gitbook/assets/image (91).png" alt="" data-size="original"> |
| LTX2\_video\_vae\_bf16.safetensors                                | [https://huggingface.co/Kijai/LTX2.3\_comfy ](https://huggingface.co/Kijai/LTX2.3_comfy) | <img src="../.gitbook/assets/image (90).png" alt="" data-size="original"> |
| gemma\_3\_12B\_it\_fp8\_e4m3fn.safetensors                        | https://huggingface.co/GitMylo/LTX-2-comfy\_gemma\_fp8\_e4m3fn                           | <img src="../.gitbook/assets/image (92).png" alt="" data-size="original"> |
| ltx-2.3-spatial-upscaler-x2-1.1.safetensors                       | [https://huggingface.co/Lightricks/LTX-2.3 ](https://huggingface.co/Lightricks/LTX-2.3)  | <img src="../.gitbook/assets/image (93).png" alt="" data-size="original"> |

## 실행

1. 제공된 `AWS_MZC_I2V` 워크플로를 로딩합니다.
2.  Queue를 실행하여 아웃풋을 생성합니다.

    ![I2V 워크플로](../.gitbook/assets/image36.png)
