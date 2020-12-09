###### 본 글은 한림대학교 클라우드컴퓨팅 수업 최종 결과 제출물을 위한 글 입니다.   
## 클라우드컴퓨팅 텀 프로젝트 : UE4 & CLOUD Multi Maze Runner

#### 0. 목차
    1. 개요
      * 프로젝트 명
      * 프로젝트 멤버 이름 및 담당 파트
    2. 프로젝트 소개
      * 전체 소개
      * 개발 내용
      * 결과물 소개 (+ 다이어그램)
    3. 사용 방법 소개
    4. 필요성 및 활용 방안

## 1. 개요
### 1.1. 프로젝트 명
 < UE4 & CLOUD > Multi Maze Runner (멀티 메이즈 러너)

### 1.2. 프로젝트 멤버 이름 및 담당 파트
20165308 김재혁 : 개발 및 적 AI 구현   
20163329 홍현준 : 개발 및 서버 구현

## 2. 프로젝트 소개
### 2.1. 전체 소개 
언리얼엔진4 를 사용해 멀티 플레이 게임을 만들고, 클라우드 서비스를 활용하여 멀티 플레이를 위한 서버를 구성하였습니다.   
언리얼엔진으로는 2명 이상의 플레이어가 경쟁하는 미로 탈출 게임을 만들었으며, 클라우드 서비스로는 아마존의 AWS를 사용하여 구성하였습니다.   

![게임 전체 뷰](https://github.com/kimjhj11/CloudComputing_TermProject_Final/blob/main/image/gameView.png?raw=true)   
-> 미로 탈출 게임
![AWS](https://github.com/kimjhj11/CloudComputing_TermProject_Final/blob/main/image/aws.PNG?raw=true)
-> AWS

### 2.2. 개발 내용
#### 2.2.1. 언리얼 엔진 멀티 플레이 구현
언리얼 엔진을 활용하여 기본적인 멀티 플레이 환경을 구현하였습니다.   
처음에는 참여자가 호스트를 배정받는 피어 투 피어(p2p) 방식으로 구현하였고,   
최종적으로는 데디케이트 서버를 포함한 클라이언트-서버 방식으로 멀티 플레이를 완성하였습니다.   

![p2p](https://github.com/kimjhj11/CloudComputing_TermProject_IntermediateResults/blob/main/image/p2p_steam.png?raw=true)   
-> 언리얼엔진 멀티플레이
   
#### 2.2.2. 멀티 플레이 서버를 클라우드 서비스로 대체
언리얼 엔진에서 멀티 플레이를 구성하면서 만든 데디케이트 서버를 기존에 예정했던대로, 아마존의 클라우드 서비스인   
AWS를 활용하여, AWS의 서비스 중 하나인 EC2 서비스를 사용하여 클라우드 서버를 구성하였습니다.   

![EC2](https://github.com/kimjhj11/CloudComputing_TermProject_Final/blob/main/image/ins.PNG?raw=true)   
-> 아마존 AWS EC2 

#### 2.2.3. 언리얼 엔진 멀티 플레이를 활용한 게임 구현
클라우드 서버를 성공적으로 구현하였기에 이제는 단순히 언리얼 엔진 레벨안에서 만나는 것이 아닌, 2명 이상의 사람들이 즐길 게임이 필요합니다.   
거대한 미로에서 많은 적들을 뚫고 달리는 영화에서 착안하여, 앞길을 알 수 없는 미로와 플레이어를 공격하는 구체형 로봇이 존재하는 미로를 제작하여   
이 미로를 먼저 탈출하는 사람이 게임에서 승리하는 멀티플레이 경쟁 게임을 만들었습니다.

![미로 게임 뷰](https://github.com/kimjhj11/CloudComputing_TermProject_Final/blob/main/image/mazegame.png?raw=true)
-> 제작 게임 : Multi Maze Runner

### 2.3. 결과물
#### 2.3.1. 클라우드 서버   
AWS EC2 서비스를 사용하여 클라우드 서버를 구동중입니다.

![클라우드 서버](https://github.com/kimjhj11/CloudComputing_TermProject_Final/blob/main/image/EC2_1.png?raw=true)   
-> 클라우드 서버

#### 2.3.2. 게임 세부 사항
서로 다른 플레이어 스타트 포인트에서 시작하여 레벨 중간에 존재하는 유리벽 등을 통해서 서로의 진행 상황을 대략적으로 파악할 수 있으며,   
최후에는 미로 마지막에서 구체형 로봇 적에게 둘러쌓인 공간에서 각자의 미로가 서로 한길로 이어져 서로를 밀어내며 결승선으로 달리는 경쟁 게임 입니다.

![미로](https://github.com/kimjhj11/CloudComputing_TermProject_Final/blob/main/image/maze2.PNG?raw=true)

#### 2.3.4. 게임 적 AI
미로에서 등장하는 구체형 로봇 적의 AI를 구현하였습니다. 각각의 AI가 존재하기에 각자의 루트에서 순찰을 하다가 자신의 감시 범위에 플레이어들이 감지되면,   
감지 범위에서 벗어나기 전까지 플레이어를 추적하고 플레이어와 접촉하면 플레이어 각각의 HP가 사라지고 만약 자신의 HP가 0이 되면 게임은 종료되고 패배합니다.   

![적AI](https://github.com/kimjhj11/CloudComputing_TermProject_Final/blob/main/image/enemy.PNG?raw=true)    
![적AI2](https://github.com/kimjhj11/CloudComputing_TermProject_Final/blob/main/image/enemy2.PNG?raw=true) 
![적AI3](https://github.com/kimjhj11/CloudComputing_TermProject_Final/blob/main/image/ai.png?raw=true)
-> 적 AI 인식 범위 테스트 블루프린트 

#### 2.3.5. 프로젝트 다이어그램

![다이어그램](https://github.com/kimjhj11/CloudComputing_TermProject_Final/blob/main/image/d1.PNG?raw=true)   
-> EC2 가상서버 구현 다이어그램   
![다이어그램1](https://github.com/kimjhj11/CloudComputing_TermProject_Final/blob/main/image/d2.PNG?raw=true)   
-> 스팀 플러그인 다이어그램

## 3. 사용 방법
### 3.1. 게임 실행
패키징된 게임을 실행하면 다음과 같은 메인화면이 존재합니다.   
메인화면에서 게임을 접속하거나 혹은 옵션에서 접속할 서버의 아이피 설정이 가능합니다.

![메인화면](https://github.com/kimjhj11/CloudComputing_TermProject_Final/blob/main/image/main.png?raw=true) 

### 3.2. 서버 접속
옵션에서 접속할 서버의 아이피 설정을 하고 게임 서버에 접속합니다.   
이 예제에서는 AWS EC2로 만든 클라우드 서버가 게임서버가 되기에 EC2 아이피를 설정하여 접속합니다.
*아래 스크린샷에서는 임의 ip를 임시로 할당하였습니다.

![ip설정](https://github.com/kimjhj11/CloudComputing_TermProject_Final/blob/main/image/ip.png?raw=true) 

### 3.3. 플레이!
이제 플레이 하는 것만 남았습니다.   
친구를 부르고 미로에서 경쟁하면 됩니다.

![미로경쟁](https://github.com/kimjhj11/CloudComputing_TermProject_Final/blob/main/image/play.PNG?raw=true)

## 4. 필요성 및 사용 방안
### 4.1. 필요성
본 프로젝트는 소규모의 인원에서 멀티플레이 게임을 만들어 서버를 클라우드로 구성하여 게임을 제작하였습니다.   
게임 서버를 클라우드로 구성함으로써 게임을 실행하기전 특정 컴퓨터를 사용하여 서버를 구동하는 리소스와 불편함을 줄이고 편리성은 높혀줍니다.
   

### 4.2 사용 방안

소규모 혹은 인디 게임을 만드는 팀에서는 게임 서버에 접속할 인원을 예측하기 힘드므로 혹시 모를 큰 상황에 대비한다는 것은 인원적으로도, 자원적으로도 어려운 일 입니다.   
개인 혹은 팀의 컴퓨터를 계속 혹사시키기 보다는, 보다 유연하게 대처할 수 있는 클라우드 서버를 사용하는 것이 더 나은 판단일 수도 있습니다.    
   
***
   
지금까지 < UE4 & CLOUD > Multi Maze Runner 프로젝트의 최종 보고서 였습니다.

  <pre><code>
  패키징 하지 않은 프로젝트의 전체 용량이 90기가가 초과하기에(언리얼 엔진을 포함하여)
  프로젝트를 다운받을 수 있는 외부링크로 대체합니다.
  감사합니다.
  </code></pre>
  
  *AWS EC2를 활용한 미로 게임 : <http://naver.me/5Dhx2BPD>   
  *AWS EC2를 활용한 미로 게임(스팀 서버를 활용한 기능도 포함)  : <http://naver.me/5Rrm9DwG>   
  *두 프로젝트의 내용은 동일합니다. 스팀 서버 플러그인 기능의 유무 차이 입니다.   
  
###### 20165308 김재혁 / 20163329 홍현준
