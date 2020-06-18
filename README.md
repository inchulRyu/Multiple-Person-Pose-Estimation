## OpenPose 이용한 Multiple-Person Pose Estimation(MPPE)
### WINDOWS 환경에서 실시함.
### (CUDA와 CUDNN는 사전에 설치할 것)

### 방법1)

https://github.com/CMU-Perceptual-Computing-Lab/openpose/releases 에서 <br>
"openpose-1.6.0-binaries-win64-gpu-python-flir-3d_recommended.zip"(gpu 이용할 시) 혹은 
"openpose-1.6.0-binaries-win64-only_cpu-python-flir-3d.zip"(cpu만 이용할 시) 다운받기



원하는 위치에 압축을 풀기<br>
PowerShell 실행<br>
```
cd 압축을 푼 경로

ex.
cd C:\Users\UserName\Desktop\openpose-1.6.0-binaries-win64-gpu-python-flir-3d_recommended
```
를 입력하여 작업경로를 바꿔주기<br>
압축푼 폴더에서 examples\media에 원하는 영상파일을 넣은 후 

```
bin\OpenPoseDemo.exe --video examples\media\영상파일이름.확장자

ex.
bin\OpenPoseDemo.exe --video examples\media\video.avi
```
를 입력하면 OpenPose가 실행된다.
