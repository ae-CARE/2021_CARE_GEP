# Video_to_CSV 동작
* RUN_video_to_csv.py 실행하여 동작(input은 내부 코드 참고)
* q 버튼 = 다음 영상, a 버튼 = 종료
* 다른 영상 경로에 대해서 실행할 수 있도록 수정 필요

# Vecterization모듈 구상 및 개요
## 개요
1. 외부에서 호출하여 사용하는 용도
## input
* 학습용:
1. 인풋 dir 은 무조건 AI..로 시작해야 함!
* 추론용: 
1. (-1, 3) 형태의 np.array of 관절 keypoint 값(row - 관절 명, column - x, y, z)
2. csv 저장용 랜덤 폴더 디렉토리 ex) '~/csv_for_server/[current time].csv'

## output:
* 학습용:
1. Normalization, 거리 및 각도 정보 새로 쓴 csv파일
1-1. 내부 연산을 np.array로 (-1,3) 모양으로 하다보니, output csv파일에 2차원배열형태로 써진다. 추출 시 참고!
* 추론용:
1. N개 프레임 마다의 csv파일
2. 해당 프레임의 Normalization, 거리 및 각도 정보 리스트 리턴

1. 관절 각도-1(서로 떨어진 벡터 각도)
2. 관절 각도-2(붙어있는 벡터 각도)
3. 관절 간 거리


## 필요사항...
1. 각도라는 것. 두 벡터 사이의 각도보다... 달리는 것 = 허벅지 벡터의 어떠한 z축 과의 움직이는 각도 변화가 중요함.
2. np.array reshape 후 연산 진행, list로 저장. csv저장 시 어떻게 저장되는지 확인 필요
3. size 다른 csv파일에 대한 keypoint 맞춤 진행

# Json_to_CSV_class 설명
## 기억할 것
* 2019 AI_hub 데이터의 경우, bbox 정보는 x,y, width, height 가 아니라, 좌 상단 xy, 우 하단 xy임에 유의할 것
## 개요
1. 일회성으로 csv생성하는 py. 동작 예시 내부 작성해놓음
 
