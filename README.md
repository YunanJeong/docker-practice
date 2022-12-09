# container-practice

---
# [도커 종류, 라이센스, 설치용어, 히스토리 정리](https://github.com/YunanJeong/docker-practice/blob/main/docker_license_history.md)

---
# 도커 설치 방법 (Ubuntu)
## 공식 & 최신 Docker Engine (docker-ce)
- **Apache 2.0 License**
	- [출처(공식)](https://docs.docker.com/engine/#licensing)
	- [git출처(공식)](https://github.com/moby/moby/blob/master/LICENSE)
	- 사람들이 많이쓰는, 회사에서도 사용가능한 버전
- [ubuntu에서 설치방법(공식)](https://docs.docker.com/engine/install/ubuntu/)
	- 레포지토리 등록 후 apt install
	- 또는, deb패키지파일을 다운받아서 설치
- docker-ce는 현재 공식명칭은 아니지만, 여전히 Docker Engine을 관례적으로 가리키는 말이다.
	- 위 공식 방법으로 설치해도 패키지명은 docker-ce로 표기된다.
- [WSL에서 설치시 참고(init vs. systemd)](https://github.com/YunanJeong/linux-tips/blob/main/wsl-service-init-vs.systemd/README.md)
	- Docker Engine은 백그라운드로 항상 실행되는 프로세스로, 현재 작동 유무 체크를 위해 서비스 관리자가 필요

## docker.io
- 구버전
- Debian/Ubuntu의 apt repository에 제공된 docker 릴리즈 이름
- 편하게 설치가능한 것이 장점. 간단한 컨테이너 사용시 별 문제없고 사용법도 거의 동일
```
$ sudo apt update
$ sudo apt install docker.io
```

---
# 용어
- Container(컨테이너)
	- 앱 및 앱 실행 환경을 하나의 패키지로 격리하는 기술
- Container Runtime(컨테이너 런타임)
	- 컨테이너 관리도구
	- 여러가지 있으나 Docker로 사실상 표준화
	- Docker로 만든 Container는 표준이 지켜져 있기 때문에 다른 Container Runtime에서도 사용가능
- Container Orchestration(컨테이너 오케스트레이션)
	- 여러 호스트에 걸친 Container들을 관리하는 행위

- Docker(도커)
	- 사실상 표준 Container Runtime
	- vm처럼 image 개념을 사용
	- DockerFile을 작성하여 image로 build 가능
	- DockerFile이나 image가 여러 host, 여러 사람들 간에 공유되곤 한다.
	- *Registry*: 도커 이미지 관리 공간. 기본적으로 Docker Hub로 설정되어 있어, 인터넷으로 편하게 공유가능
	- *Repository*: Registry 내 도커 이미지 저장공간. 이미지 이름으로 여기는게 더 직관적이다.
	- *Tag*: 동일한 repository(이름)의 이미지들을 구분하는 용도로 사용. 주로 버전이 표기되는 자리

- Docker Compose(도커 컴포즈)
	- (하나의 호스트에서) 여러 Container들을 관리하는 도구
		- 한 호스트 내 한정이라는 점 때문에, Orchestration Tool로는 취급되지 않는 편
	- Docker 프로젝트에 통합되어 있으며 `docker compose`라는 subcommand 형태로 사용 가능
	- docker-compose라는 패키지가 별도로 존재하나, 구버전
	- Docker Compose는 yaml파일에 모든 Container 설정들을 기술해두고, up&down 명령어만 사용하면 돼서 편하다.
	- Docker만 사용시 개별 Container를 `docker run ...` 명령어로 관리해야해서, 관리할 Container 수가 조금만 늘어나도 불편하다. 이럴 때 Docker Compose가 용이하다.

- Docker Swarm(도커 스웜)
	- Docker 자체 제공 Container Orchestration Tool
		- (Docker Engine-based Native Docker Orchestration Tool)
		- `docker swarm` 이라는 subcommand로 사용
	- 상대적으로 다루기 쉬운편이나, 잘 쓰이지 않음
- Kubernetes(쿠버네티스)
	- 약어: k8s(케이츠, 케이에이츠), kube(큐브)
	- Container Orchestration Tool의 사실상 표준
	- 구글에서 만듦






