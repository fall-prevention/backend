# 통신 구조 (Communication Architecture)
본 시스템은 **oneM2M 기반 IoT 아키텍처**를 사용하여 낙상 감지 데이터를 수집하고 전달합니다.

사물(Device)은 **TAS(Thing Adaptation Software)** 를 통해 **&Cube IoT Device Platform**에 연결되며,
&Cube는 **oneM2M 표준 REST API**를 이용하여 **Mobius(CSE, IoT Server Platform)** 와 통신합니다.

AI 기반 낙상 감지 시스템은 카메라 영상을 실시간으로 분석하여 이벤트를 생성하고,
낙상 발생 시 Mobius에 데이터를 저장하며 웹 애플리케이션으로 실시간 이벤트를 전달합니다.


<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/b3f24623-e8b0-4322-914b-fc541566a6c0" />

# 데이터 흐름 (Data Flow)
```
Camera
   ↓
AI Fall Detection
   ↓
TAS (&Cube)
   ↓  (oneM2M API)
Mobius (CSE)
   ↓
Backend Server
   ↓
Frontend Web (Monitoring)
```
# 통신 방법 (Communication Protocols)
본 시스템은 oneM2M 표준에서 지원하는 다양한 통신 프로토콜을 사용합니다.

- HTTP
  - Mobius 리소스 생성 및 데이터 조회
- MQTT
  - IoT 디바이스 이벤트 및 낙상 알림 전송
- CoAP
  - 저전력 IoT 환경 지원
- WebSocket / SSE
  - 웹 클라이언트 실시간 이벤트 전달
