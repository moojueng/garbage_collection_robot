# 🤖 Garbage Collection Robot - Can Detection (캔 인식 모듈)

이 저장소는 자율주행 쓰레기 수거 로봇 프로젝트의 **알루미늄 캔 인식(Can Detection)** 파트입니다.
YOLOv8 모델을 사용하여 실시간으로 캔을 탐지하고 분류합니다.

## 📂 파일 설명 (Files)
- **`best.pt`**: 학습이 완료된 AI 모델 가중치 파일입니다. (mAP50 0.96 달성, 캔 인식용)
- **`Untitled5.ipynb`**: Google Colab에서 진행한 데이터셋 다운로드 및 모델 학습 전체 코드입니다.

---

## 🛠️ 환경 설정 (Setup)
별도의 설정 파일 없이 아래 명령어로 필요한 라이브러리를 한 번에 설치할 수 있습니다.

```bash
pip install ultralytics roboflow opencv-python numpy torch torchvision

🚀 실행 방법 (How to Run)
1. 모델 불러오기 및 추론 (Python)
로봇의 메인 코드에서 best.pt 파일을 불러와 아래와 같이 사용합니다.

from ultralytics import YOLO
import cv2

# 1. 학습된 모델 로드 (같은 폴더에 best.pt가 있어야 함)
model = YOLO('best.pt')

# 2. 웹캠으로 실시간 테스트 (0번 카메라)
# 실행 시 화면에 캔 인식 결과가 표시됩니다. 'q'를 누르면 종료됩니다.
model.predict(source='0', show=True)

# 3. (옵션) 이미지나 영상 파일에서 추론할 경우
# results = model('path/to/image.jpg')

📊 데이터셋 및 학습 정보 (Dataset & Training)
이 모델은 Roboflow의 공개 데이터셋을 사용하여 Colab(T4 GPU) 환경에서 학습되었습니다.

데이터셋 출처: Roboflow Universe - Can Detection (can-iewc4)

학습 모델: YOLOv8s (Small)

학습 횟수(Epochs): 100

이미지 크기: 640x640


📝 참고 사항
Untitled5.ipynb 파일을 열어보면 데이터셋 다운로드부터 학습까지의 전 과정을 확인할 수 있습니다.

로봇(Jetson Nano/Orin 등) 환경에 따라 PyTorch 설치 버전이 다를 수 있으니, 실행이 안 되면 PyTorch 버전을 확인해주세요.
