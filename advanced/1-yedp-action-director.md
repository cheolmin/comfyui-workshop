# #2-1. Yedp Action Director

![Yedp Action Director](../.gitbook/assets/image55.png)

첫 번째로 실습할 워크플로우는 Yedp Action Director 입니다. FBX 혹은 GLB 포맷의 3D 애니메이션 데이터를 로딩하고 확인할 수 있는 뷰포트를 제공합니다. 카메라 레졸루션, Frame Count, fps를 조정할 수 있으며 설정한 카메라 세팅으로 Openpose, Depth, Canny, Normal 컨트롤넷 패스를 렌더링 할 수 있습니다.

Mixamo 애니메이션 데이터와 완벽하게 호환되며, 비디오 생성용 소스로 활용할 수 있습니다.

## 워크플로 로딩

1. 제공된 `AWS_MZC_Yedp_Action_Director.json` 워크플로를 로딩합니다.
2.  Missing Custom 노드를 설치합니다. ComfyUI Manager → **Install Missing Custom Nodes** 클릭.

    <figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>


3.  **ComfyUI-VideoHelperSuite**를 설치합니다.

    ![VideoHelperSuite](../.gitbook/assets/image7.png)
4.  정상적으로 로딩된 워크플로를 확인합니다. 로딩할 애니메이션은 `..\ComfyUI\input\yedp_anims` 폴더에 존재해야 합니다.

    ![워크플로 확인](../.gitbook/assets/image17.png)

    <figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>



## Mixamo 애니메이션 다운로드

1. https://www.mixamo.com/ 으로 이동하여 Adobe 계정으로 로그인합니다.
2.  원하는 애니메이션을 선택 후 **Download** 클릭 → 다운로드 세팅 확인 후 Download.

    ![Mixamo 다운로드](../.gitbook/assets/image19.png)

    ![다운로드 세팅](../.gitbook/assets/image28.png)
3.  UI 화면 우측 하단 Upload Model을 클릭하여 팝업 창을 띄운 뒤, Upload 탭에서 Target Directory를 input/yedp\_anims로 설정한 후 Select File에서 파일 선택 후 fbx 파일을 업로드합니다.

    <figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

## Yedp Action Director 노드 파라미터

| 파라미터                                                | 설명                         |
| --------------------------------------------------- | -------------------------- |
| animation                                           | 로딩할 애니메이션                  |
| width / height                                      | 화면 너비/높이 값                 |
| frame\_count                                        | 로딩할 프레임 수                  |
| fps                                                 | 프레임 레이트 설정값                |
| Depth (beta)                                        | 프리뷰를 Depth 컨트롤넷으로 변경       |
| N, F                                                | Near, Far - 적정한 Depth 값 설정 |
| Bake                                                | 프리뷰 화면 그대로 컨트롤넷 포즈를 베이킹    |
| SYNC FOLDERS                                        | 애니메이션 데이터가 있는 폴더와 동기화      |
| BAKE FRAMES                                         | 현재 프레임을 베이크합니다.            |
| Transform, Camera, Lighting, Character, Environment | 커스텀 파일을 업로드해서 제어할 수 있는 기능  |

## 실행

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>



1.  워크플로는 Yedp\_action\_director에서 베이킹 후 큐를 실행해 배치 렌더를 생성하는 방식으로 작동합니다. 카메라를 세팅한 뒤 **Bake**를 클릭하여 베이킹합니다.<br>

    <figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>
2.  **Run** 클릭 혹은 `Ctrl+Enter`로 Queue를 실행합니다. 각각 Openpose, Depth, Normal, Canny 컨트롤넷 비디오가 생성됩니다.<br>

    <figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
