![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9aaacb51-7af0-4ad2-9983-74c58f95655d/c995625b-1681-48fa-b097-3a84fc1acb53/Untitled.png)

## 딥러닝 네트워크 분류

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9aaacb51-7af0-4ad2-9983-74c58f95655d/a719589c-bddc-4f2c-bd19-4c975c9865e1/Untitled.png)

- **1-Stage Detector** (YOLO, SSD …)
  - localization과 classification이 동시에 이루어집니다. 객체의 위치와 종류를 동시에 예측하는 단일 신경망 모델입니다.
- **2-Stage Detector** (RCNN, Faster R-CNN, …)
  - localization과 classification이 따로 이루어집니다. 먼저 후보 영역을 추출한 후, 추출된 영역에 대해 localization과 classification을 수행하는 두 개의 단계로 구성됩니다.

### **Classification (분류)**

- 분류는 이미지가 어떤 클래스에 속하는지를 결정하는 작업
- 일반적으로 softmax 함수와 cross-entropy loss를 사용하여 수행되며, 결과적으로 각 클래스에 대한 확률 분포를 제공합니다.

### **Localization (위치 추정)**

- 이미지 내의 특정 객체의 위치를 찾는 작업
- bounding box(경계 상자) 형태로 표현되며, bounding box는 이미지 내에서 객체가 존재하는 영역을 사각형으로 표현.
- Localization은 보통 회귀 문제로 처리되며, 네트워크는 bounding box의 좌표(x, y)와 너비 및 높이(w, h)를 예측하게 됩니다.

## 각 모델별 특징과 장단점

| 모델         | 특징                                                         | 장점                                                       | 단점                                                |
| ------------ | ------------------------------------------------------------ | ---------------------------------------------------------- | --------------------------------------------------- |
| YOLO         | 실시간 객체인식에 적합한 모델                                | 빠른 속도, 높은 정확도 (상대적 낮음)                       | 작은 객체에 대한 정확도 저하                        |
| SSD          | 다양한 크기의 객체 탐지에 특화                               | 높은 정확도, 실시간 처리 가능                              | 작은 객체에 대한 정확도 저하                        |
| Faster R-CNN | 정확한 객체 위치 추정을 위한 RPN 활용                        | 높은 정확도                                                | 처리 속도가 상대적으로 느림                         |
| Mask R-CNN   | 객체의 위치와 세분화된 마스크 생성 가능                      | 정확도와 세분화된 결과 생성에 우수                         | 처리 속도가 상대적으로 느림                         |
| EfficientDet | 경량화된 모델이지만 높은 정확도 제공                         | 경량화와 높은 정확도의 조합                                | 최근에 개발된 모델로 인해 상대적으로 연구가 진행 중 |
| EfficientNet | 복잡성과 리소스 사용 사이에서 균형인 성능 확보를 위해 설계됨 | 경량화되면서 고성능. 다양한 크기에서 일관성 있는 성능 제공 | 최근에 개발된 모델로 인해 상대적으로 연구가 진행 중 |

- **YOLO(You Only Look Once)**: 실시간 객체 탐지에 적합하며, 한 번의 순방향 패스만으로 객체를 탐지할 수 있습니다. 그러나 작은 객체를 탐지하는 데 있어서 일부 한계가 있을 수 있습니다.
- **SSD(Single Shot MultiBox Detector)**: 다양한 크기의 객체를 탐지하는 데 특화되어 있으며, 여러 가지 크기의 default box (또는 anchor box)를 사용하여 다양한 크기와 비율의 객체를 탐지합니다. 하지만 역시 작은 객체에 대한 인식률이 상대적으로 낮을 수 있습니다.
- **Faster R-CNN**: Region Proposal Network(RPN)을 사용하여 후보 영역을 추출하고 이 영역들에 대해 분류와 바운딩 박스 좌표 회귀를 동시에 수행합니다. 높은 정확도를 보여주나 처리 속도가 상대적으로 느립니다.
- **Mask R-CNN**: Faster R-CNN 위에 세그멘테이션(segmentation) 마스크 생성 branch를 추가한 구조입니다. 따라서 개별 객체 인식 외에도 해당 개체가 차지하는 영역까지 세밀하게 구분할 수 있는 장점이 있습니다. 그러나 복잡한 구조로 인해 처리 속도는 상대적으로 느릴 수 있습니다.
- **EfficientDet**: EfficientNet과 같은 자동화된 아키텍처 검색(AutoML 및 Compound Scaling) 기법을 이용하여 경량화되면서도 높은 성능을 보여줍니다. 최신 기술로 연구가 진행 중인 단계입니다.
- **EfficientNet:** 이미지 분류 문제를 해결하기 위해 설계되었으며, Compound Scaling 방법인 네트워크 너비, 깊이, 그리고 이미지 해상도를 동시에 조정함으로써 계산 복잡성과 리소스 사용 사이에서 균형인 성능을 확보하는 것이 목표입니다.

**결론**

차량 탐지에 가장 유용한 모델은 YOLO입니다. YOLO는 실시간 객체 탐지에 적합하며, 한 번의 순방향 패스만으로 객체를 탐지할 수 있습니다. 그러나 작은 객체를 탐지하는 데 있어서 일부 한계가 있을 수 있습니다. 따라서 차량 탐지에 최적인 모델은 YOLO입니다.

---

### ref

https://nuguziii.github.io/survey/S-001/

https://tech.socarcorp.kr/data/2020/02/13/car-damage-segmentation-model.html
