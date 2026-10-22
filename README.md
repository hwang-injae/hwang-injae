# 황인재 · Injae Hwang

로봇 SW 개발자(신입)입니다. 협동로봇(Doosan M0609 · P3020)과 AMR(TurtleBot4)로 팀 Project 4건을 했고, 초기 설계와 전체 기능 통합, Vision과 로봇의 연동을 맡았습니다.

<a href="https://hwang-injae.github.io/"><img src="assets/website.svg" width="40" alt="포트폴리오 웹사이트"></a>&nbsp;
<a href="mailto:il1282113@gmail.com"><img src="assets/gmail.svg" width="40" alt="Gmail"></a>&nbsp;
<a href="https://www.linkedin.com/in/hwang-injae/"><img src="assets/linkedin.svg" width="40" alt="LinkedIn"></a>

## 지금까지

국립부경대학교 화학과 졸업을 앞두고 있습니다. AI를 로봇에 접목해 보고 싶어 방향을 바꿨고, 두산로보틱스 ROKEY 9기(2026.04 ~ 2026.10)에서 Python · Computer Vision · ROS 2 · 협동로봇 · 지능형 로봇을 배우며 팀 Project 4건을 마쳤습니다.

요즘은 두 가지를 하고 있습니다.

- 팀 Project에서 제가 맡지 않았던 부분(MoveIt2 경로 계획, 두산 힘 제어, Nav2 순찰)의 코드를 다시 읽으며 동작 원리를 정리하고 있습니다.
- 2026년 12월부터 C++와 rclcpp로 ROS 2 노드를 작성하는 공부를 시작합니다.

## 써 본 기술

| 분야 | 기술 |
|---|---|
| 로봇 | ROS 2 Jazzy · MoveIt2 · Nav2 · Doosan M0609 · P3020 · TurtleBot4 · Isaac Sim 5.1 · Lula IK · Gazebo |
| Vision · AI | YOLO(seg) · OpenCV · MediaPipe · NumPy |
| Web · Data | FastAPI · Next.js · three.js · PostgreSQL · SQLite · MQTT · Docker |
| 언어 · 도구 | Python · TypeScript · pytest · Ubuntu · Git |

## Projects

### [BuildMind — AI가 설계하고 로봇이 조립하는 젠가 가구](https://github.com/hwang-injae/buildmind)

사람이 글이나 말로 가구를 요청하면 AI(Claude)가 젠가 블록 설계도를 만들고, 무너지지 않는지·로봇이 지을 수 있는지 검사를 통과한 설계만 DB에 세대별로 저장합니다.
두산 M0609가 흩어진 블록을 손목 카메라(**YOLO seg + 깊이**)로 찾아 **MoveIt2**로 하나씩 집어 조립하고, 사람이 쌓은 구조물을 스캔해 똑같이 복제할 수도 있습니다.

ROKEY 협동-2 · 5인 팀 · 2026.10 · Doosan M0609 + OnRobot RG2 · ROS 2 Jazzy · MoveIt2 · YOLO seg · FastAPI · Next.js · PostgreSQL · MQTT  
[Notion 정리](https://app.notion.com/p/401f5144f244818c97cbdf9a395181ca)

<table>
  <tr>
    <td width="50%" align="center"><img src="https://raw.githubusercontent.com/hwang-injae/buildmind/main/docs/images/demo/%EB%8D%B0%EB%AA%A8_AI%EC%84%A4%EA%B3%84%EC%83%9D%EC%84%B1_v1_101715.gif" width="100%" alt="말로 요청 → Claude 설계 후보 3개 → 3D 미리보기"><br><sub>요청 → AI 설계 후보 → 3D 미리보기</sub></td>
    <td width="50%" align="center"><img src="https://raw.githubusercontent.com/hwang-injae/buildmind/main/docs/images/demo/%EB%8D%B0%EB%AA%A8_%EC%8A%A4%EC%BA%94%EB%B3%B5%EC%A0%9C_v1_101715.gif" width="100%" alt="스캔한 구조물을 같은 자리 · 방향 · 모양으로 복제 조립"><br><sub>스캔한 구조물을 그대로 복제 조립</sub></td>
  </tr>
</table>

**담당 역할: PL · HMI(웹 화면 · AI 설계 생성 · 설계 DB · MQTT 브리지) · YOLO seg 학습**
- **AI 설계 생성**: 웹 PC의 Claude Code를 호스트 중계(`claude_bridge`)로 불러 설계도 후보 3개를 만들게 했습니다. JSON Schema 구조화 출력으로 형식 실패 0, 검사를 통과하지 못하면 실패 원인을 AI에 다시 전달해 최대 2번 다시 생성합니다.
- **설계 DB 세대 관리**: PostgreSQL에 설계를 부모·버전으로 이어 저장하고, 같은 Template의 설계를 AI가 골라 참고하는 RAG를 적용했습니다(파생 설계 15개·3세대).
- **웹 화면 · MQTT 브리지**: Next.js + three.js 화면(설계 3D 미리보기·손목 카메라·로봇 패널), 로봇 PC와 웹 PC를 잇는 MQTT 브리지, 웹 PC Docker Compose 구성을 맡았습니다.
- **YOLO seg 학습 · 라벨링**: 흩어진 블록을 찾는 YOLO seg의 학습 데이터를 라벨링하고 yolo26s-seg 비교 학습을 맡았습니다(최종 모델 mAP50 0.972).
- **PL**: 일정·결정 기록·발표를 맡고, 기능 동결 뒤에는 PL 통합 브랜치(1~10차)에서 통합 테스트를 거친 버전만 main에 병합했습니다.

**결과(팀):** 통합 시험에서 흩어진 블록 집기 98%(162번 중 159번) · 스캔 복원 일치율 92% · AI 설계 형식 실패 0 · AI가 만든 설계 2종 실제 조립


### [SortTwin — AMR × 협동로봇 택배 분류 디지털 트윈](https://github.com/hwang-injae/amr-cobot-sorting)

Isaac Sim으로 만든 물류 디지털 트윈입니다. 입고 AMR → 협동로봇(P3020) 상차 → 컨베이어 → 휠소터 분류(권역 A·B·C · 불량) → 두 번째 협동로봇의 불량품 적재까지 전 공정을 한 미션으로 연결했습니다.

ROKEY 협동-3 · 4인 팀 · 2026.08 · Isaac Sim 5.1 · ROS 2 Jazzy · Lula IK  
[Notion 정리](https://app.notion.com/p/401f5144f24481e4a4a8dcf259c55da4)

<img src="https://raw.githubusercontent.com/hwang-injae/amr-cobot-sorting/main/docs/screenshots/top-view-x5.gif" width="640" alt="Warehouse Top View — AMR, P3020, Conveyor, Wheel Sorter 전체 공정">

**담당 역할: P3020 협동로봇 Pick & Place · 비전 연동**
- Pick & Place를 8단계 상태 머신으로 작성하고, IK 목표에 TCP 오프셋 보정과 관절 안전 한계를 넣었습니다.
- 팀원이 만든 YOLO 검출 결과와 Depth로 박스 윗면의 3D 좌표를 구하고, 거리·색상·높이 3단 필터로 그리퍼·그림자·AMR 몸체 오탐을 걸렀습니다.
- Isaac Sim 내장 Python(3.11)에서 ROS 2 커스텀 액션 서버가 실패하는 문제를, 액션 서버를 시스템 Python 프로세스로 분리하고 토픽으로 잇는 방식으로 해결했습니다.
- 불량품 라인(P3020 OUT)은 입고 쪽 IK·상태 머신·비전 로직을 재사용해 작성하고, 적재 계획 모듈(`OutboundLoadPlanner`)을 실제 에이전트에 처음 연결했습니다.


### [PreWash-Cell — 다회용기 예비세척 자동화 셀](https://github.com/hwang-injae/prewash-cell)

두산 M0609 협동로봇이 반납된 다회용 그릇·컵을 집어 잔반을 털고, 안쪽을 힘 제어로 닦아 식기세척기 팔레트에 꽂는 자동화 셀입니다.
카메라 없이 **파지 폭 · 무게 · 힘**만으로 판단합니다.

ROKEY 협동-1 · 4인 팀 · 2026.09 · Doosan M0609 + OnRobot RG2 · ROS 2 Jazzy · FastAPI · Next.js · SQLite  
[Notion 정리](https://app.notion.com/p/401f5144f2448190b54bd0d5fa624d30)

<table>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/hwang-injae/prewash-cell/main/docs/images/demo/demo_cup_wipe.gif" height="240" alt="컵 안쪽을 솔로 위아래 · 손목 회전하며 닦기"><br><sub>컵 안쪽 닦기(2배속)</sub></td>
    <td align="center"><img src="https://raw.githubusercontent.com/hwang-injae/prewash-cell/main/docs/images/demo/demo_nudge_resume.gif" height="240" alt="멈춘 로봇팔을 손으로 가볍게 밀어 재개"><br><sub>멈춘 팔을 가볍게 밀어 재개</sub></td>
  </tr>
</table>

**담당 역할: PM · 인터페이스 · 운영 화면(HMI) · 기록 DB · 셀 통합 · 무게 측정 안정화**
- 팀원이 찾은 문제(ROS 서비스 콜백 안에서 두산 API를 부르면 멈춤)를 실제 드라이버로 다시 확인하고, 실행 구조 5가지를 비교 시험해 구조 변경을 결정했습니다. 기능 사이 인터페이스(`contracts.py`)를 먼저 고정해 4명이 로봇 1대를 나눠 쓰면서도 각자 개발할 기준을 만들었습니다.
- 운영 화면(시작·일시정지·재개·중단, 멈춤 원인 안내, 누적 통계)과 SQLite 기록 DB를 맡았습니다.
- 셀 통합과 실기 운용을 맡아 기능 동결 시점과 "기본 흐름은 유지하고 예외 처리만 고친다"는 원칙을 정했고, 무게 측정값이 출렁이는 원인(그리퍼 케이블 장력)을 찾아냈습니다.

**결과(팀):** 배속 1.0에서 그릇 2개·컵 2개를 사람 개입 없이 무정지 완주(약 13분, 9/29 실기) · 예외 7종 실기 복구(빈 구역 건너뛰기 포함)


### [IDC Patrol — TurtleBot4 2대 협동 순찰 MVP](https://github.com/hwang-injae/idc-patrol-robot)

TurtleBot4 2대가 미니 IDC(랙 56기)를 나눠 순찰하며 열린 랙 도어는 YOLO로, 랙 번호는 ArUco 마커로 판별해 관제 웹에 보고하는 팀 MVP입니다. 로봇 2대 분담 SLAM 매핑 · 지도 병합과 실제 카메라의 도어 검출까지 시연했습니다.

ROKEY 지능-1 · 8인 팀 · 2026.09 (6일) · ROS 2 Jazzy · TurtleBot4 · Nav2 · YOLO  
[Notion 정리](https://app.notion.com/p/401f5144f24481d0bfd7d69a1d37d514)

<img src="https://raw.githubusercontent.com/hwang-injae/idc-patrol-robot/main/docs/images/demo.gif" width="640" alt="랙 도어 YOLO 검출과 로봇 2대 매핑 화면">

**담당 역할: PM(프로젝트 매니저) — 시스템 구성도 · 설계 문서 · 일정 · 데이터**
- 설계 문서(SDD)의 최신 결정을 반영해 PC 4대 전체 구성도(draw.io)와 발표용 파트별 구성도 3종(AMR·Vision·관제)을 작성하고, 요구사항·설계 문서(BRD·SRD·SDD) 작성과 개정에 참여했습니다.
- 9/7부터 팀원별 할 일을 정해 알리고, 진행 상황을 받아 일정을 조정했습니다.
- 라벨링 환경과 초기 라벨링 가이드·검수 규칙을 만들고, 도어 열림/닫힘 데이터 수집과 라벨링에 참여했습니다.

## 그 밖의 실습

Project 사이사이에 한 실습과 팀 미니 Project입니다. 자세한 내용은 각 저장소 README에 있습니다.

| 프로젝트 | 내용 · 담당 | 스택 | 저장소 |
|---|---|---|---|
| 손 제스처로 켜고 끄는 물체 추적 로봇 | 보자기 → 출발, 주먹 → 정지. 빨간 공을 장애물처럼 보고 가까워질수록 감속해 목표 거리에서 정지하는 추적 제어 (팀 프로젝트 · 2026.07 ~ 08) · **담당 역할: 상태 · 이동 제어, 단위 테스트** | ROS 2 · OpenCV · MediaPipe · turtlesim · Gazebo | [gesture-controlled-robot-tracking](https://github.com/hwang-injae/gesture-controlled-robot-tracking) |
| M0609 기어 조립 DRL → ROS 2 | 티치 펜던트 DRL 동작을 ROS 2 Python으로 옮겨 실제 로봇에서 완주 (협동-1 사전 실습 · 개인) | Doosan M0609 · RG2 · 힘 제어 | [rokey-mini-projects](https://github.com/hwang-injae/rokey-mini-projects/tree/main/m0609-gear-drl-to-ros2) |
| Isaac Sim M0609 색상 분류 | 카메라 영상에서 큐브 색을 판별해 로봇팔이 마커로 옮기게 하는 ROS 2 색 감지 노드 (협동-3 사전 실습 · 4인) · **담당 역할: 색 감지 노드 수정 · Isaac Sim 연동** | Isaac Sim · ROS 2 · OpenCV | [rokey-mini-projects](https://github.com/hwang-injae/rokey-mini-projects/tree/main/isaac-m0609-color-sort) |
| TurtleBot4 RC카 탐색 · 추적 | 고정 웹캠이 RC카를 찾으면 TurtleBot4가 출동해 회전 탐색 · 추종하는 미션 (지능-1 미니 프로젝트 · 4인) · **담당 역할: 객체 탐지(YOLO11n · ByteTrack)** | TurtleBot4 · Nav2 · YOLO | [rokey-mini-projects](https://github.com/hwang-injae/rokey-mini-projects/tree/main/tb4-rc-car-search-track) |

## 연락

메일 주시면 바로 답장드리겠습니다.

<a href="https://hwang-injae.github.io/"><img src="assets/website.svg" width="40" alt="포트폴리오 웹사이트"></a>&nbsp;
<a href="mailto:il1282113@gmail.com"><img src="assets/gmail.svg" width="40" alt="Gmail"></a>&nbsp;
<a href="https://www.linkedin.com/in/hwang-injae/"><img src="assets/linkedin.svg" width="40" alt="LinkedIn"></a>
