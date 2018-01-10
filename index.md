---
#
# Here you can change the text shown in the Home page before the Latest Posts section.
#
# Edit cayman-blog's home layout in _layouts instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
#
layout: 
---

## 태진아 할아버지는...  

태진아*(#뉴비 #게이머 #마음만은 #초고수)*씨는  
올해 66세가 되었지만 손자와 게임을 하기 위해 컴퓨터를 배우고 있다.  

하지만 '요즘 것들'의 채팅 속도를 따라잡기가 어렵다. 타자 연습 프로그램으로 이용해보았지만, 실력이 는다는 느낌이 안든다.  

그런데!!!  

한달 뒤, 태진아 할아버지는 현란한 손놀림으로 채팅을 하게 된다.  
무슨 일이 벌어진 것일까?  

## 태진아 할아버지가 이용한 것은!?  

안녕하세요, **'전자석을 이용한 타자 연습기'**를 개발한 경희대학교 전자공학과 **Khu Key board**입니다.  

저희는 키보드와 웨어러블 장갑의 전자석을 달아, 전자석 사이의 인력을 사용자가 인지하며 키보드 타이핑을 할 수 있는 타자 연습기를 설계, 개발하였습니다.  

그럼 저희 프로젝트에 대해 자세히 소개해보도록 하겠습니다.
  

## X-Corps 페스티벌 자료

<iframe src="//www.slideshare.net/slideshow/embed_code/key/5ufcCT1AmzDzm5" width="100%" height="500px" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe>

## 프로토타입 소개 및 시연 영상  
  
<iframe width="100%" height="300px" src="https://www.youtube.com/embed/ZEWkTbEnWDc" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

 
## 시스템 구성도  

![](https://github.com/sauber92/GraduationProject-Doc/blob/master/Documentation/Reference/Diagram/system.png?raw=true)  

**전자석을 이용한 타자 연습기**는 컴퓨터 응용프로그램인 *Typing Assistant*와 키보드 위에 올려놓고 사용하는 *Keyboard Panel*, 장갑형태의 *FingerTip*으로 이루어져있습니다.  


## 시퀀스 다이어그램  

![](https://github.com/sauber92/GraduationProject-Doc/blob/master/Documentation/Reference/Diagram/sequence.png?raw=true)  

**과정 1,2**: 전원이 KP와 FT에 인가되면 KP와 FT은 서로 블루투스 연결을 맺는다. TA는 어플리케이션이 실행될 때 2초의 로딩시간을 거치면서 KP와 FT의 블루투스 연결이 맺어지는 것을 기다린다.  

**과정 3,4**: TA와 KP가 시리얼 연결을 맺는다.  

**과정 5,6**: TA는 입력해야 할 문자를 무작위로 생성한 후 모니터에 출력한다.  

**과정 7,8:** TA는 생성된 문자를 Character형으로 시리얼 통신을 통해 KP로 전달하고 KP는 이에 해당하는 전자석을 활성화한다.  

**과정 9,10**: KP는 TA로 부터 받은 문자를 블루투스 통신을 통해 FT으로 전달하고 FT은 이에 대항하는 전자석을 활성화한다.  

**과정 11**: 사용자가 KP와 FT의 전자석의 전자기력을 인지하고 키보드를 올바르게 입력하면 키보드 인터럽트 이벤트가 발생한다.  

**과정 12~15**: 키보드 인터럽트가 발생하면 KP와 FT의 전자석을 비활성화한다.  

**과정 16**: TA는 다시 새로운 문자를 무작위로 생성한 후 위의 과정을 반복한다.  


***

## Typing Assistant  

![](https://github.com/sauber92/GraduationProject-Doc/blob/master/Documentation/Reference/Diagram/tp.png?raw=true)

TA는 Node.js 엔진과 Chromium 브라우져을 기반으로 데스크탑 어플리케이션을 제작할 수 있는 [Electron](https://electron.atom.io/)을 사용하여 만들어졌습니다.  

[node-serialport 모듈](https://github.com/EmergingTechnologyAdvisors/node-serialport)을 사용하여 KP과 시리얼 통신을 할 수 있게 하였으며, 자체적으로 랜덤하게 영어 소문자 하나를 생성하고, 그에 해당하는 키보드 인터럽트 이벤트가 발생하면 다시 새로운 문자가 생성니다.  

### 개발스펙  

* IDE: WebStorm (Ver. 2016.3.2)  
* NPM: Ver 4.2.0
* Node: Ver 7.10.0  
* Electron: Ver 1.4.1  
* electron-installer-dmg: Ver 0.2.1  
* electron-rebuild: Ver 1.4.0  
* electron-winstaller: Ver 2.5.2  
* Dependencies  
	* app: 0.1.0  
	* electron-packager: 8.7.0  
	* path: 0.12.7  
	* serialport: 4.0.7  

### Release  

* Mac 버전: [dmg파일](https://github.com/sauber92/GraduationProject-TA/releases/tag/1.0.0)  
	* macOS Sierra 10.12.5에서 확인  
* Windows 버전: [exe파일](https://github.com/sauber92/GraduationProject-TA/releases/tag/1.0.1)  
	* Windows 10 Pro 1703에서 확인
	* Pre-release: 설치파일의 생성을 못해서 Pre-release 버전으로 실행파일만 배포

### Git Repository  

[https://github.com/sauber92/GraduationProject-TA](https://github.com/sauber92/GraduationProject-TA)

***

## Keyboard Panel  

![](https://github.com/sauber92/GraduationProject-Doc/blob/master/Documentation/Reference/Diagram/KP.png?raw=true)  

Arduino Mega 보드와 16채널 릴레이 2개, 전자석 26개를 사용하여 구성하였습니다. 블루투스 모듈은 HC-06을 사용했습니다.  

[SoftwareSerial 라이브러리](https://www.arduino.cc/en/Reference/softwareSerial)를 통해 FT과 블루투스 통신을 하였습니다.  

### 개발스펙  

* IDE: Arduino Sketch (Ver. 1.8.2)  
* Arduino Mega ADK
	* SoftwareSerail library  

### Git Repository  

[https://github.com/sauber92/GraduationProject-KP](https://github.com/sauber92/GraduationProject-KP)

***

## FingerTip

![](https://github.com/sauber92/GraduationProject-Doc/blob/master/Documentation/Reference/Diagram/FT.png?raw=true)  

Arduino Uno 보드와 4채널 릴레이 2개, 전자석 8개를 사용하여 구성하였습니다. 블루투스 모듈은 HC-06을 사용했습니다.  

[SoftwareSerial 라이브러리](https://www.arduino.cc/en/Reference/softwareSerial)를 통해 KP과 블루투스 통신을 하였습니다.  

### 개발스펙  

* IDE: Arduino Sketch (Ver. 1.8.2)  
* Arduino Uno
	* SoftwareSerail library  

### Git Repository  

[https://github.com/sauber92/GraduationProject-FT](https://github.com/sauber92/GraduationProject-FT)

***

## 프로젝트 관리  

[Khu Key board의 트렐로](https://trello.com/b/TO1BCMvY)  
