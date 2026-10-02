<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=24&pause=1000&color=22C3E6&center=true&vCenter=true&width=560&lines=Physical+AI+%26+Robotics+Software;ROS+2+%7C+Computer+Vision+%7C+Cobots" alt="typing banner" />
</p>

<h1 align="center">Hi there, I'm Injae Hwang 👋</h1>

<br>

## About Me

- 🎓 **국립부경대학교 화학과 졸업 예정**입니다.
- 🧪 지금은 **Physical AI · 로보틱스 소프트웨어** 분야로 커리어를 전환하고 있습니다.
- 💡 AI가 사회를 빠르게 바꾸는 모습을 보며 AI를 더 깊이 공부하고 싶어졌고, AI가 실제 세계에서 움직이는 로보틱스로 방향을 정했습니다.
- 🤖 **두산로보틱스 ROKEY 부트캠프**에서 Python, Computer Vision, ROS 2, 협동로봇·지능형로봇 프로그래밍을 학습하고 있습니다. (2026.04 ~ 2026.10)
- 🔨 부트캠프에서 팀 프로젝트를 진행하며 실무 흐름을 익히고 있습니다.

<br>

## 🎯 Focus / Keywords

`Physical AI` · `Robotics` · `ROS 2` · `Collaborative Robots` · `Intelligent Robots` ·
`Robot Manipulation` · `Computer Vision` · `Deep Learning`

<br>

## 🌱 Currently Learning

- ROS 2 (topics, services, actions, launch) — Python
- 협동로봇 / 지능형로봇 프로그래밍
- NVIDIA Isaac Sim 기반 로봇 시뮬레이션
- OpenCV 기반 이미지 처리 · 객체 인식
- PyTorch 기반 딥러닝 인식(perception)

<br>

## 🛠️ Tech Stack

**Robotics**<br>
![ROS 2](https://img.shields.io/badge/ROS_2-22314E?style=for-the-badge&logo=ros&logoColor=white)
![Gazebo](https://img.shields.io/badge/Gazebo-F58113?style=for-the-badge&logoColor=white)
![Isaac Sim](https://img.shields.io/badge/Isaac_Sim-76B900?style=for-the-badge&logo=nvidia&logoColor=white)

**Vision**<br>
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)
![MediaPipe](https://img.shields.io/badge/MediaPipe-0097A7?style=for-the-badge&logo=mediapipe&logoColor=white)

**Language · Tools**<br>
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=for-the-badge&logo=pytest&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)

<br>

## 🚀 Main Projects

ROKEY 9기 정규 팀 프로젝트입니다.

### [PreWash-Cell — 다회용기 예비세척 자동화 셀](https://github.com/hwang-injae/rokey_9_pjt1_D2)

두산 M0609 협동로봇이 반납된 다회용 그릇·컵을 집어 잔반을 털고, 안쪽을 힘 제어로 닦아 식기세척기 팔레트에 꽂는 자동화 셀입니다.
카메라 없이 **파지 폭 · 무게 · 힘**만으로 판단합니다.

`ROKEY 협동-1` · `4인 팀` · `2026.09` · `Doosan M0609 + OnRobot RG2` · `ROS 2 Jazzy` · `FastAPI · Next.js · SQLite`

<img src="https://raw.githubusercontent.com/hwang-injae/rokey_9_pjt1_D2/main/docs/images/hmi_running.png" width="640" alt="PreWash-Cell 운영 화면">

**담당: PM · 인터페이스 · 운영 화면(HMI)·기록 DB · 셀 통합**
- 두산 Python API가 ROS 콜백 안에서 멈추는 문제를 재현·확인하고, 실행 구조 5가지를 비교해 구조 변경을 결정했습니다. 기능 사이 인터페이스(`contracts.py`)를 먼저 고정해 4명이 로봇 1대를 나눠 쓰면서도 각자 개발할 기준을 만들었습니다.
- 운영 화면(시작·일시정지·재개·중단, 멈춤 원인 안내, 누적 통계)과 SQLite 기록 DB를 맡았습니다.
- 셀 통합과 실기 운용을 맡아 기능 동결 시점과 "기본 흐름은 유지하고 예외 처리만 고친다"는 원칙을 정했고, 무게값이 출렁이는 원인(그리퍼 케이블 장력)을 찾아냈습니다.

**결과(팀):** 배속 1.0에서 그릇 2개·컵 2개를 사람 개입 없이 무정지 완주(약 13분, 9/29 실기) · 예외 6종 복구와 빈 구역 건너뛰기 실기 확인

<br>

### [AMR × 협동로봇 택배 분류 디지털 트윈](https://github.com/hwang-injae/cobot3-ws-c2)

Isaac Sim으로 만든 물류 디지털 트윈입니다. 입고 AMR → 협동로봇(P3020) 상차 → 컨베이어 → 휠소터 분류(권역 A/B/C·불량) → 두 번째 협동로봇의 불량품 적재까지 전 공정을 한 미션으로 연결했습니다.

`ROKEY 협동-3` · `4인 팀` · `2026.08` · `Isaac Sim 5.1` · `ROS 2 Jazzy` · `Lula IK`

<img src="https://raw.githubusercontent.com/rokey-c2/cobot3-ws-c2/main/docs/screenshots/top-view-x5.gif" width="640" alt="Warehouse Top View — AMR, P3020, Conveyor, Wheel Sorter 전체 공정">

**담당: P3020 협동로봇 Pick & Place · 비전 연동**
- Pick & Place를 8단계 상태 머신으로 작성하고, IK 목표에 TCP 오프셋 보정과 관절 안전 한계를 넣었습니다.
- 팀원이 만든 YOLO 검출 결과와 Depth로 박스 윗면의 3D 좌표를 구하고, 거리·색상·높이 3단 필터로 그리퍼·그림자·AMR 몸체 오탐을 걸렀습니다.
- Isaac Sim 내장 Python(3.11)에서 ROS 2 커스텀 액션 서버가 실패하는 문제를, 액션 서버를 시스템 Python 프로세스로 분리하고 토픽으로 잇는 방식으로 해결했습니다.
- 불량품 라인(P3020 OUT)은 입고 쪽 IK·상태 머신·좌표 계산 로직을 재사용해 작성하고, 팔에서 먼 칸부터 2×2로 채우는 적재 순서를 적용했습니다.

<br>

### [IDC 순찰로봇 — TurtleBot4 2대 협동 순찰 MVP](https://github.com/hwang-injae/rokey_idc_patrol)

TurtleBot4 2대가 미니 IDC(랙 56기)를 순찰하며 열린 랙 도어는 YOLO로, 랙 번호는 ArUco 마커로 판별해 관제 웹에 보고하는 것을 목표로 한 팀 MVP입니다.

`ROKEY 지능-1` · `8인 팀` · `2026.09 (1주)` · `ROS 2 Jazzy` · `TurtleBot4 · Nav2` · `YOLO`

<img src="https://raw.githubusercontent.com/hwang-injae/rokey_idc_patrol/main/docs/images/demo.gif" width="640" alt="랙 도어 YOLO 검출과 로봇 2대 매핑 화면">

**담당: PM(프로젝트 매니저) — 설계 문서 · 일정 · 데이터**
- 요구사항·설계 문서(BRD·SRD·SDD) 작성과 개정에 참여하고, 시나리오가 바뀔 때 PL과 함께 일정을 다시 짰습니다. 통합 테스트 전에 파트별 단위 테스트 7개 항목을 일정에 넣었습니다.
- 라벨링 환경과 초기 라벨링 가이드·검수 규칙을 만들고, 도어 열림/닫힘 데이터 수집과 라벨링에 참여했습니다.
- YOLOX nano·s 후보 모델을 학습했습니다.

<br>

## 🧪 Mini Projects

큰 프로젝트 사이사이에 장비와 도구를 익히며 진행한 미니프로젝트와 스터디 프로젝트입니다. → [rokey-mini-projects](https://github.com/hwang-injae/rokey-mini-projects)

| 미니프로젝트 | 내용 | 스택 | 상태 |
|---|---|---|---|
| [M0609 기어 조립: DRL → ROS 2 Python](https://github.com/hwang-injae/rokey-mini-projects/tree/main/m0609-gear-drl-to-ros2) | 티치 펜던트로 만든 기어 조립 동작을 ROS 2 Python 노드로 옮기며 달라진 점을 고쳐 실제 로봇에서 완주 | Doosan M0609 · DSR_ROBOT2 · 힘제어 | ✅ |
| [Isaac Sim M0609 색상 분류](https://github.com/hwang-injae/rokey-mini-projects/tree/main/isaac-m0609-color-sort) | 로봇팔 카메라 영상에서 큐브 색을 판별하는 ROS 2 색 감지 노드 (협동-3 사전 실습 · 담당: 팀원이 만든 노드를 파랑·초록 시나리오에 맞게 수정하고 Isaac Sim과 연동) | Isaac Sim · ROS 2 · OpenCV | ✅ |
| [TurtleBot4 RC카 탐색·추적](https://github.com/hwang-injae/rokey-mini-projects/tree/main/tb4-rc-car-search-track) | 웹캠이 RC카를 인식하면 AMR이 출동해 회전 탐색 후 추종 (4인 팀 · 담당: 웹캠 RC카 인식) | TurtleBot4 · Nav2 · YOLO11n | 🟡 미완성 |
| [Gesture-Controlled Robot Tracking](https://github.com/hwang-injae/gesture-controlled-robot-tracking) | 손 제스처로 로봇의 물체 추적을 시작·정지 (ROKEY 스터디 5인 팀 · 담당: 상태·이동 제어 — 비례 제어, 상태 머신, 안전 정지, pytest) | ROS 2 · OpenCV · MediaPipe | ✅ |

<br>

## 📫 Connect

[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:il1282113@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/hwang-injae/)

<!-- 공개 저장소에 커밋이 쌓이면 아래 주석을 풀어 통계 카드를 활성화하세요
## 📊 GitHub Stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=hwang-injae&show_icons=true&theme=tokyonight&hide_border=true&include_all_commits=true" alt="github stats" />
  <img src="https://github-readme-streak-stats.herokuapp.com?user=hwang-injae&theme=tokyonight&hide_border=true" alt="streak" />
</p>
<p align="center">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=hwang-injae&layout=compact&theme=tokyonight&hide_border=true" alt="top languages" />
</p>
-->
