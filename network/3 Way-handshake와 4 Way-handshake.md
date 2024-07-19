# 3 Way-handshake와 4 Way-handshake

`TCP는 애플리케이션에게 신뢰적이고 연결지향성 서비스를 제공`한다. 따라서, **서버와 클라이언트간에 데이터를 신뢰성 있게 전달하기 위해 만들어진 프로토콜**이다. 그리고 `TCP는 장치들 사이에 논리적인 접속을 성립하기 위해서 3-way handshake를 사용`한다.

<br>
<br>

## 3-Way Handshake 
**TCP/IP 프로토콜을 이용해서 통신을 하는 응용프로그램이 데이터를 전송하기 전에 먼저 정확한 전송을 보장하기 위해 상대방 컴퓨터와 사전에 세션을 수립하는 과정**을 말한다.
3-way handshake는 `양쪽 모두 데이터를 전송할 준비가 되어있다는 것을 보장`하고, 실제로** 데이터 전달이 시작하기 전에 다른 한쪽이 준비**되었다는 것을 알 수 있도록 해준다.

<br>
<br>

## 3-way handshake의 동작방식

#### 1. **[Client -> SYN -> Server]**
Client가 Server에게 접속을 요청하는 SYN플래그를 보낸다.

#### 2. **[Server -> SYN + ACK -> Client ]**
Server는 Listen 상태에서 SYN이 들어온 것을  확인하고 SYN_RECV상태로 바뀌어 SYN + ACK 플래그를 클라이언트에게 전송. 그 후 Server는 다시 ACK 플래그를 받기 위해 대기 상태로 변경

#### 3. **[Client -> ACK -> Server]**
SYN + ACK 상태를 확인한 클라이언트는 서버에게 ACK를 보내고 연결 성립이 된다.
 
<br>
<br>

##  4 Way-handshake의 동작방식
4 Way-handshake는 연결을 종료하기 위해 수행되는 절차이다.

#### 1. **[Client -> FIN -> Server]**
Client가 연결을 종료하겠다는 FIN플래그를 전송한다. 보낸 후에 FIN-WAIT-1 상태로 변한다.

#### 2. **[Server -> FIN -> Client]**
FIN 플래그를 받은 Server는 확인메세지인 ACK를 Client에게 보내준다. 그 후 CLOSE-WAIT 상태로 변한다. Client도 마찬가지로 Server에서 종료될 준비가 됐다는 FIN을 받기위해 FIN-WAIT-2 상태가 된다.

#### 3. **[Server -> FIN -> Client]**
CLOSE 준비가 다 된 후 Server는 Client에게 FIN 플래그를 전송한다.

#### 4. **[Client -> ACK-> Server]**
Client는 해지 준비가 되었다는 정상응답인 ACK를 Server에게 보내준다. 이 때, Client는 TIME-WAIT 상태로 변경된다.

<br>
<br>

여기서 TIME-WAIT 상태는 의도치않은 에러로 인해 연결이 데드락으로 빠지는 것을 방지하기 위해 변경 되는 것인데, 만약 에러로 인해 종료가 지연되다가 타임이 초과되면 CLOSED 상태로 변경된다.
