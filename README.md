
이 저장소는 진명아이엔씨 현장실습 기간 동안 연구한 낙상 탐지 모델을 구현한 코드입니다.

## 0. 폴더 설명
<pre>
project
|-- mim: pretrained mmpose model
|-- mmpose
|-- net egru
|   |--pretrained:pretraiend model
|   |--model:egru.net
|-- stgcn
|   |--feeder:preprocess
|   |--tools: preprocess 
|-- yolox
|-- bytetrack
|-- bot-sort
</pre>

## ⚙️ 서버 및 환경 설정

- **GPU 환경**: RTX A6000 (0,1번 GPU, 총 2개 사용)  
- **실행 서버**: 회사 내 GPU 서버 및 교내 서버 활용  
- **CUDA 버전**: 11.8  
- **환경 설정**: 동일한 환경에서는 `requirements.txt`를 참고하여 세팅 가능  

### 사용 모델
- **Detection & Tracking**: BoT-SORT, ByteTrack, YOLOX-mot17  
- **Pose Estimation**: OpenPose, MMPose  
- **Inference (행동 인식)**: ST-GCN, EGRU  


## 🚀 demo 1) BoT-SORT + MMPose + ST-GCN
<img width="1208" height="671" alt="image" src="https://github.com/user-attachments/assets/6cdd23b0-def6-40db-9c0b-02083645ed06" />

**구현 과정**  
1. **BoT-SORT** : Re-ID 기반 추적을 통해 track_id별 bbox 정보 추출  
2. **MMPose** : 각 프레임의 track 단위 Skeleton 추출  
3. **ST-GCN** : Skeleton 시퀀스를 입력으로 Falling Inference 수행  


---   

## 🚀 demo 2) ByteTrack + extract feature +  EGRU


https://github.com/user-attachments/assets/c7584c28-4662-4ef4-9120-45d6de85acac

https://github.com/user-attachments/assets/7eb9e400-7580-40dc-bdf2-d8e0dd79a52b

**구현 과정**  
1. **ByteTrack** : track_id별 bbox 정보 추출  
2. **Feature Extract** : Bounding Box 기반 피처(cx, cy, vx, vy, Δaspect 등) 계산  
3. **EGRU** : Temporal Feature 기반 Falling Inference 수행


---   

## 🚀 demo 3) ByteTrack + ENSEMBLE(EGRU/ST-GCN)




https://github.com/user-attachments/assets/b3c13540-f2db-42a8-8ff4-a582fb7e5d39




**구현 과정**  
1. **ByteTrack** : track_id별 bbox 정보 수집  
2. **MMPose** : Skeleton Feature 추출  
3. **Fusion (EGRU + ST-GCN)** : BBox Feature + Skeleton Feature 융합, Ensemble Inference 실행  

---.

