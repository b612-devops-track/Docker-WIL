### 컨테이너 서비스

컨테이너 : 어떤 사물을 격리할 수 있는 공간 </br>

컨테이너 기술은 최신 기술이 아니나, [2013년 현재의 컨테이너 가상화 기술 표준이 됨] </br>

애플리케이션 개발환경이 도커 기반의 컨테이너 서비스 환경으로 전환됨 </br>

하드웨어 레벨 가상화: 하이퍼바이저 등을 이용한 가상머신의 방식 </br>

운영체제 레벨 가상화: 컨테이너 기반의 애플리케이션 서비스 방식 [호스트 운영체제를 공유하고 애플리케이션에 필요한 환경을 패키징하는 것] </br>

```bash
1. 애플리케이션 코드 개발
2. 베이스 이미지를 이용한 Dockerfile 작성
3. Dockerfile build를 통한 새로운 이미지 생성 
4-1. 생성된 이미지를 이용한 컨테이너 실행 
4-2. 도커컴포즈를 이용한 다중 컨테이너 실행 : 도커 실행 옵션을 미리 작성한 docker-compose.yml을 통해
     다중 컨테이너 간 실행 순서, 네트워크, 의존성 등을 통합 관리 할 수 있고 마이크로 서비스 개발에 활용된다.
5-1. 컨테이너 애플리케이션 서비스 테스트 : Nginx를 이용한 웹 애플리케이션 컨테이너 서비스였다면 연결하는 IP와 포트 번호를 이용하여
     웹 브라우저를 이용한 페이지 연결을 확인할 수 있다.
5-2. 마이크로서비스 테스트 
6. 로컬 및 원격 저장소에 이미지 저장(push) 
7. 깃허브 등을 활용한 Dockerfile 관리 
8. 동일 환경에서의 지속적 애플리케이션 개발 수행
```

  이미지를 실행하면 애플리케이션 컨테이너

```bash
  docker pull 명령 옵션
  --all-tags, -a  저장소에 태그로 지정된 여러 이미지를 모두 다운로드 함.
  --disable-content-trust 이미지 검증 작업 건너뛰기, DCT를 이용한 이미지 신뢰성 검증, 작업으로 DOCKER_CONTENT_TRUST=1로 활성화
    (비활성화, 0)
  --platform      플랫폼 지정, 윈도우 도커에서 리눅스 이미지를 받아야 하는 경우 사용.
  --quiet, -q     이미지 다운로드 과정에서 화면에 나타나는 상세 출력 숨김.
```