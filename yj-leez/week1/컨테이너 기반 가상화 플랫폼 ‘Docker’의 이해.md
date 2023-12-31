# 컨테이너 기반 가상화 플랫폼 ‘Docker’의 이해 1강

강의에 사용되는 도커 이미지 pull 받기 : https://bit.ly/docker-sk

### 도커의 등장

- Docker는 이미지를 통해서 다양한 환경을 제공

### 컨테이너

- 컨테이너는 다른 환경을 제공한다는 점에서 가상머신과 비슷하지만 같지 않음
    - VM은 소프트웨어로 구현된 하드웨어, but 컨테이너는 하드웨어 가상화가 없는 격리된 환경에서 실행되는 프로세스
    - 리눅스 커널에서 제공하는 프로세스 격리하는 기능을 사용하는 격리된 프로세스
        <img width="476" alt="1" src="https://github.com/yj-leez/Docker-WIL/assets/77960090/e0ba1e68-c4a9-48b4-89ec-0377467e308e">

        
- 도커가 나오기 전에는루트 디렉토리를 바꿔주는 역할을 하는 chroot을 사용함

### 이미지

- 특정 프로세스를 실행하기 위한 환경
    - 계층화된 파일 시스템
    - 이미지는 파일들의 집합, 프로세스가 실행되는 환경도 결국 파일들의 집합

### 도커 기본 아키텍처
<img width="453" alt="2" src="https://github.com/yj-leez/Docker-WIL/assets/77960090/f7280d79-f091-44ae-a251-77ec09667506">

- 리눅스 머신 : 컨테이너를 네이티브하게 지원, 실제 도커 컨테이너 배포에는 리눅스 머신을 사용

<img width="453" alt="3" src="https://github.com/yj-leez/Docker-WIL/assets/77960090/1d586d91-4989-4003-88a1-5f4938612592">

- Docker for macOS: xhyve라는 경량 가상 머신을 사용하여 컨테이너 실행, 호스트 머신처럼 사용가능

<img width="453" alt="4" src="https://github.com/yj-leez/Docker-WIL/assets/77960090/a72e433d-dfe2-4999-82f0-20c2e35be61f">

- VM on macOS : 일반적인 가상머신, 호스트 프로세스처럼 작동하지 않고 가상머신의 프로세스로 작동

### 컨테이너 가상화가 필요한 이유

보편적이지 않은 컴퓨터 환경을 보완하기 위한 기술로, 이미지로 만들면 어디서나 같은 환경을 확실하게 공유할 수 있음을 보장 가능
