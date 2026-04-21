# Mesh Chat Pro

**P2P 실시간 채팅 + 파일 전송 · WebRTC 기반 · 서버 불필요**

![License](https://img.shields.io/badge/license-MIT-blue)
![Version](https://img.shields.io/badge/version-1.0-green)

---

## 🎯 특징

✅ **서버 없는 P2P** — 브라우저 간 직접 연결  
✅ **내부망 + 외부망** — STUN/TURN으로 모든 환경 지원  
✅ **개인 메시지(DM)** — 1:1 채팅 지원  
✅ **파일 전송** — 최대 100MB 지원  
✅ **실시간 알림** — 데스크톱 알림 + 제목 깜빡임  
✅ **최대 10명** — 그룹 채팅 안정성  
✅ **한글 지원** — 방 이름/닉네임 완전 지원  

---

## 🚀 빠른 시작

### 방법 1: 웹에서 바로 사용
1. [🔗 index.html을 브라우저에서 열기](https://raw.githubusercontent.com/[당신의repo]/index.html)
2. 닉네임 입력
3. "Create Room" 또는 "Join Room"

### 방법 2: 로컬에서 사용
```bash
# 저장소 복제
git clone https://github.com/[당신의username]/mesh-chat-p2p.git
cd mesh-chat-p2p

# 브라우저에서 index.html 열기
open index.html  # macOS
start index.html # Windows
```

---

## 💬 사용법

### 방 만들기
```
1. "Create Room" 탭
2. 방 이름 입력 (예: 팀 회의)
3. 참여 코드 입력 (예: team01)
4. (선택) 비밀번호 설정
5. "Create Room" 클릭
6. 참여 코드를 친구들과 공유
```

### 방 참가하기
```
1. "Join Room" 탭
2. 친구가 공유한 참여 코드 입력
3. (필요시) 비밀번호 입력
4. "Join Room" 클릭
```

### 기본 조작
| 기능 | 방법 |
|------|------|
| 메시지 전송 | Enter |
| 줄바꿈 | Shift+Enter |
| 파일 첨부 | 📎 파일 첨부 버튼 |
| 개인 메시지 | 왼쪽 멤버 목록에서 클릭 |
| 참여 코드 복사 | Copy 버튼 |

---

## 🔧 기술 스택

- **WebRTC** — P2P 실시간 통신
- **PeerJS** — WebRTC 래퍼 라이브러리
- **JavaScript (Vanilla)** — 의존성 없음
- **HTML5 + CSS3** — 모던 UI

### 네트워크 서버
- **STUN**: Google (무료)
  - `stun:stun.l.google.com:19302`
  - `stun:stun1.l.google.com:19302`
  - `stun:stun2.l.google.com:19302`
  - `stun:stun3.l.google.com:19302`

- **TURN**: Open Relay Project (무료)
  - `turn:openrelay.metered.ca`
  - 자동으로 기업망/모바일 NAT 우회

---

## 📋 지원 환경

| 브라우저 | 버전 | 상태 |
|---------|------|------|
| Chrome | 74+ | ✅ 완전 지원 |
| Firefox | 55+ | ✅ 완전 지원 |
| Safari | 12.1+ | ✅ 완전 지원 |
| Edge | 79+ | ✅ 완전 지원 |

### 시스템 요구사항
- 최신 브라우저
- 인터넷 연결
- 마이크/스피커 (선택)

---

## ⚙️ 고급 설정

### 커스텀 시그널링 서버 (선택)
기업 환경에서는 자체 시그널링 서버 사용 가능:

```javascript
// index.html에서 initPeer 함수 수정
peer = new Peer(cId, {
  host: 'your-server.com',
  port: 9000,
  path: '/peerjs'
});
```

### 파일 크기 제한 변경
```javascript
// index.html에서 onFile 함수 수정
if(f.size > 500*1024*1024) { // 500MB로 변경
  err("File max 500MB");
  return;
}
```

---

## 🚨 제한사항

- ⚠️ **최대 10명** — 그룹 채팅 안정성 위해 제한
- ⚠️ **100MB 파일** — 그 이상은 자동 거부
- ⚠️ **브라우저 종료** — 전송 중단
- ⚠️ **방화벽** — 극단적인 회사 방화벽은 우회 불가

---

## 🔐 보안

- **종단간 암호화** — 서버를 거치지 않음
- **비밀번호 보호** — 방 참가 시 인증
- **로컬 저장** — 메시지는 로컬에만 저장
- **HTTPS 권장** — 배포 시 HTTPS 사용

---

## 🤝 기여

버그 리포트 또는 기능 추가 제안:
```bash
# Fork → Clone → Commit → Push → Pull Request
```

---

## 📄 라이선스

MIT License - 자유롭게 사용, 수정, 배포 가능

---

## 📞 문제 해결

### "방을 찾을 수 없습니다"
- 참여 코드를 정확히 입력했는지 확인
- 호스트(방 생성자)가 여전히 접속해 있는지 확인
- 네트워크 연결 확인

### "연결 실패"
- 브라우저를 새로고침 (F5)
- 다른 브라우저 시도
- 개발자 도구(F12) 콘솔에서 에러 메시지 확인
- 방화벽 설정 확인

### "파일이 안 받아집니다"
- 파일 크기가 100MB 이하인지 확인
- 수신자가 여전히 연결되어 있는지 확인
- 다시 전송 시도

---

## 📊 성능

- **지연시간**: 100-300ms (같은 지역)
- **처리량**: 파일 전송 1-5Mbps (TURN 경유 시 느림)
- **동시 접속**: 10명 안정

---

## 🎓 학습 자료

이 프로젝트는 다음을 배우기 좋습니다:
- WebRTC 기초
- P2P 네트워킹
- JavaScript 비동기 처리
- 실시간 통신

---

**Made with ❤️ for P2P Communication**

Last updated: 2026-04-21
