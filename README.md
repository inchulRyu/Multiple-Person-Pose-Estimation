## OpenPose 이용한 Multiple-Person Pose Estimation(MPPE)
### WINDOWS 환경에서 실시함.


### 방법1)
https://colab.research.google.com/github/tugstugi/dl-colab-notebooks/blob/master/notebooks/OpenPose.ipynb <br>
에서 첫번째 코드셀 다음에 코드 셀을 추가하여 아래 코드 입력
```
from google.colab import files

uploaded = files.upload()

for fn in uploaded.keys():
  print('User uploaded file "{name}" with length {length} bytes'.format(
      name=fn, length=len(uploaded[fn])))
```
실행하여 추론하길 원하는 영상파일 업로드<br>
<br>
그 아래 두 개의 코드셀 삭제하기
```
YOUTUBE_ID = 'RXABo9hm8B8'


YouTubeVideo(YOUTUBE_ID)
```
이것과
```
!rm -rf youtube.mp4
# download the youtube with the given ID
!youtube-dl -f 'bestvideo[ext=mp4]' --output "youtube.%(ext)s" https://www.youtube.com/watch?v=$YOUTUBE_ID
# cut the first 5 seconds
!ffmpeg -y -loglevel info -i youtube.mp4 -t 5 video.mp4
# detect poses on the these 5 seconds
!rm openpose.avi
!cd openpose && ./build/examples/openpose/openpose.bin --video ../video.mp4 --write_json ./output/ --display 0  --write_video ../openpose.avi
# convert the result into MP4
!ffmpeg -y -loglevel info -i openpose.avi output.mp4
```
이것
<br>
그리고 코드 셀을 추가하여 아래의 코드 입력
```
!rm openpose.avi
!cd openpose && ./build/examples/openpose/openpose.bin --video ../영상파일이름.확장자 --write_json ./output/ --display 0  --write_video ../openpose.avi
# convert the result into MP4
!ffmpeg -y -loglevel info -i openpose.avi output.mp4
```
"영상파일이름.확장자"를 업로드시킨 영상파일이름.확장자로 바꾼 후 (ex. video.avi) 실행<br>
그리고 맨 아래의 코드 셀을 실행하면 추론된 영상이 나온다.<br>
왼쪽의 파일목록에서 output.mp4 를 마우스 우클릭 후 '다운로드'를 클릭하면 다운로드가 가능하다.


<br>
<br>

### 방법2)
#### CUDA와 CUDNN 사전에 설치할 것!!

https://github.com/CMU-Perceptual-Computing-Lab/openpose/releases 에서 <br>
"openpose-1.6.0-binaries-win64-gpu-python-flir-3d_recommended.zip"(gpu 이용할 시) 혹은 
"openpose-1.6.0-binaries-win64-only_cpu-python-flir-3d.zip"(cpu만 이용할 시) 다운받기



원하는 위치에 압축을 풀기<br>
PowerShell 실행<br>
```
cd 압축을 푼 경로

ex)
cd C:\Users\UserName\Desktop\openpose-1.6.0-binaries-win64-gpu-python-flir-3d_recommended
```
를 입력하여 작업경로를 바꿔주기<br><br>
압축푼 폴더에서 examples\media에 원하는 영상파일을 넣은 후 

```
bin\OpenPoseDemo.exe --video examples\media\영상파일이름.확장자

ex)
bin\OpenPoseDemo.exe --video examples\media\video.avi
```
를 입력하면 OpenPose가 실행되어 영상이 추론된다.
