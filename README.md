
# 2023_2_opensw_201812419_HW1

본 프로젝트는 경기대학교 오픈소스SW 강의의 HW1로 TensorFlow와 Docker를 활용하여 Mask R-CNN을 구현합니다. 

아래의 단계별 지침을 따라 진행해 주세요.

## 환경 설정
1. **Docker 이미지 가져오기**  
   TensorFlow GPU 버전 이미지를 pull합니다.  
   ```
   docker pull tensorflow/tensorflow:2.2.0-gpu
   ```

2. **Docker 컨테이너 실행**  
   이름이 `tensor`인 도커 컨테이너를 실행합니다.  
   ```
   docker run -dit --name tensor tensorflow/tensorflow:2.2.0-gpu
   ```

3. **Docker 컨테이너 접속**  
   실행된 `tensor` 컨테이너에 접속합니다.  
   ```
   docker exec -it tensor /bin/bash
   ```

## 필수 패키지 설치
4. **패키지 업데이트**  
   ```
   apt-get update
   ```

5. **Git 설치**  
   ```
   apt-get install git
   ```

6. **Vim 설치**  
   ```
   apt-get install vim
   ```

7. **Wget 설치**  
   ```
   apt-get install wget
   ```

## Mask R-CNN 설정
8. **홈 디렉토리로 이동**  
   ```
   cd /home
   ```

9. **Mask R-CNN GitHub 리포지토리 클론**  
   ```
   git clone https://github.com/akTwelve/Mask_RCNN.git aktwelve_mask_rcnn
   ```

10. **클론된 디렉토리로 이동**  
    ```
    cd aktwelve_mask_rcnn/
    ```

11. **`requirements.txt` 파일 수정**  
    ```
    vi requirements.txt
    ```
    - `tensorflow>=2.0.0` 항목 삭제
    - `opencv-python`을 `opencv-python==4.1.2.30`로 수정
    - `shift+;` 입력 후 `wq`와 `Enter`로 저장 후 종료

12. **필요 패키지 설치**  
    ```
    pip install -r requirements.txt
    ```

13. **Mask R-CNN 설치**  
    ```
    python setup.py clean --all install
    ```

## 데이터셋 및 가중치 파일 설정
14. **가중치 파일 다운로드**  
    ```
    wget https://github.com/matterport/Mask_RCNN/releases/download/v2.1/mask_rcnn_balloon.h5
    ```

15. **Balloon 샘플 디렉토리로 이동**  
    ```
    cd samples/balloon/
    ```

16. **데이터셋 다운로드 및 압축 해제**  
    ```
    wget https://github.com/matterport/Mask_RCNN/releases/download/v2.1/balloon_dataset.zip
    unzip balloon_dataset.zip
    ```

## Mask R-CNN 실행
17. **Balloon 샘플 실행**  
    ```
    python3 balloon.py splash --weight=../../mask_rcnn_balloon.h5 --image=balloon/val/14898532020_ba6199dd22_k.jpg
    ```

## MASK R-CNN 실행 결과
   ![Result of Balloon Execution Using Mask RCNN 1](baloon/baloon (1).png)
   
   
   