도커 개요 및 소개
===================
도커의 등장
----------
솔로몬 하이크, 파이콘 2013 라이트닝 토크   
이미지를 통해 다양한 환경 제공

컨테이너
---------
#### VM
각각의 VM은 서로 다른 환경   
하드웨어 가상화    
소프트웨어로 구현된 하드웨어    
  
  
       
#### 컨테이너
각가의 컨테이너는 서로 다른 환경  
격리된 상황에서 실행되는 프로세스  
OS에서 지원하는 기능을 사용  
격리된 환경에서 실행  

이미지
-------
특정 프로세스를 실행하기 위한 환경  
계층화된 파일 시스템  
이미지는 파일들의 집합  
프로세스가 실행되는 환경도 결국 파일들의 집합  

아키텍처
--------
#### 리눅스 머신  
컨테이너를 네이티브하게 지원  
배포판에 따라 차이는 있지만 대부분 지원  
실제 도커 컨테이너 배포에는 리눅스 머신을 사용  

  
##### Docker for macOS  
* xhyve  
macOS의 가상화 방식(경량 가상 머신)    
컨테이너 = xhyve에서 실행된 프로세스

* 호스트 머신과 자연스럽게 결합  
네트워크/볼륨 등  
호스트 머신처럼 사용 가능  

* 주의   
일반적인 가상 머신  
컨테이너 = 가상 머신의 프로세스  
네트워크/볼륨 설정이 까다로움  
클라이언트는 환경변수를 참조해서 서버에 접속  

컨테이너 가상화가 필요한 이유
----------------------------
#### Dockerfile
꺠끗한 환경으로부터 애플리케이션 실행 환경까지 최단경로     
이미지 = 작동되는 상태   
하나의 이미지는 항상 같은 환경   

#### Docker 
chroot의 확장 버전   
초강력한 포터블 앱  
하나의 이미지는 항상 같은 환경     
재현성: 이미지로 만들면 공유 가능     
