# C언어 이론

## 컴퓨터가 변수를 처리하는 방법
  * 프로그램 메모리 주소
    - 1) 컴퓨터에서 프로그램이 실행되기 위해서는 프로그램이 메모리에 적재(Load)되어야 함
    - 2) 당연히 프로그램의 크기를 충당할 수 있을 만큼의 메모리 공간이 있어야 한다.
    - 3) 일반적인 컴퓨터 운영체제는 메모리 공간을 네 가지로 구분하여 관리한다.
      + 코드 영역 - 소스코드
      + 데이터 영역 - 전역 변수, 정적 변수
      + 힙 영역 - 동적 할당 변수
      + 스택 영역 - 지역 변수, 매개변수

![process](https://t1.daumcdn.net/cfile/tistory/114A773E511554972A)

---
## 전역 변수
  * 1) 전역 변수(Global Variable)란 프로그램의 어디서든 접근 가능한 변수를 말합니다.
  * 2) main함수가 실행되기도 전에 프로그램의 시작과 동시에 메모리에 할당된다.
  * 3) 프로그램의 크기가 커질 수록 전역 변수로 인해 프로그램이 복잡해질 수 있다.
  * 4) 메모리의 데이터(Data) 영역에 적재된다.

---
## 지역 변수
  * 1) 지역변수(Local Variable)란 프로그램에서 특정한 블록(block) 에서만 접근할 수 있는 변수를 말한다.
  * 2) 함수가 실행될때 마다 메모리에 할당되어 함수가 종료되면 메모리에서 해제된다.
  * 3) 메모리의 스택(stack) 영역에 기록된다.
---
## 정적 변수
  * 1) 정적 변수(Static Variable)란 특정한 블록안에서만 접근 할 수 있는 변수
  * 2) 프로그램이 실행될 때 메모리에 할당되어 프로그램이 종료되면 메모리에서 해제된다.
  * 3) 메모리의 데이터(Data) 영역에 적재된다.
---
## 레지스터 변수
  * 1) 레지스터 변수(Register Variable)란 메인 메모리 대신 CPU의 레지스터를 사용하는 변수이다.
  * 2) 레지스터는 매우 한정되어 있으므로 실제로 레지스터에서 처리될지는 장담할 수 없다.
  > usage : register int a = 10;

---
## 함수의 매개변수가 처리될 때
  * 1) 함수를 호출할 때 함수에 필요한 데이터를 매개변수로 전달한다.
  * 2) 전달 방식은 <값에 의한 전달> 방식과 <참조에 의한 전달> 방식이 있다.
  * 3) 값에 의한 전달 방식은 단지 값을 전달하므로 함수 내에서 변수가 자유롭게 생성된다.
  * 4) 참조에 의한 전달 방식은 주소를 전달(포인터를 이용)하므로 원래의 변수 자체에 접근할 수 있다.

---
## 2차원 배열과 포인터 배열
  * 1) 2차원 배열은 굉장히 많은 목적으로 사용됨
  * 2) 행렬 데이터를 표현할 때, 그래프 알고리즘을 처리할 때 , 다수의 실생활 데이터를 처리할 때 등
  * 3) 흔히 우리가 보는 표 구조가 2차원 배열과 흡사하다.

---
## 2차원 배열
  * 2차원 배열은 1차원 배열이 중첩되었다는 의미로 [][]대괄호를 중첩하여 쓴다
    > 자료형 배열이름 [행][열] = {{값,값,값..},{값,값...},{..}...}

---
## 다차원 배열
  * 2차원 배열 이상의 다차원 배열 또한 사용할 수 있다.
  * 우리 컴퓨터는 기본적으로 화면에 2차원 형태만 출력할 수 있다.

---
## 포인터 배열
  * 포인터 배열의 구조분석
    - 1) 배열은 포인터와 동일한 방식으로 동작한다.
    - 2) 배열의 이름은 배열의 원소의 첫 번째 주소가 된다.
    - 3) 유일한 차이점은 포인터는 변수이며 , 배열의 이름은 상수이다.
  * 포인터는 연산을 통해 자료형의 크기만큼 이동한다
    - 따라서 정수(int)형 포인터는 4바이트(Bytes)씩 이동한다.

---
## 동적 메모리 할당
  * 1) 일반적으로 C언어에서 배열의 경우 사전에 적절한 크기만큼 할당해주어야 한다.
  * 2) 우리가 원하는 만큼만 메모리를 할당해서 사용하고자 한다면 동적 메모리 할당을 사용한다
  * 3) 동적이라는 말의 의미는 '프로그램 실행 도중에' 라는 의미이다.
---
## 동적메모리
  * 1) C언어에서는 malloc()함수를 이용해 원하는 만큼의 메모리를 확보할 수 있다.
  * 2) malloc() 함수는 메모리 할당에 성공하면 주소를 반환하고, 그렇지 않으면 NULL을 반환한다.
  * 3) malloc() 함수는 <stdlib.h> 라이브러리에 정의되어있다.
  > usage: malloc(할당할 바이트 크기);

  * 4) 동적으로 할당된 변수는 <힙 영역>에 저장된다.
---
## 동적 메모리 할당 중요한 점
  * 1) 전통적인 C언어에서는 스택에 선언된 변수는 따로 메모리 해제를 해주지 않아도 된다.
  * 2) 반면에 동적으로 할당된 변수는 반드시 free() 함수로 메모리 해제를 해주어야한다.
  * 3) 메모리 해제를 하지 않으면 메모리 내의 프로세스 무게가 더해져 언젠가는 오류가 발생한다.
  * 4) 메모리 누수(memory leak) 방지는 코어 개발자의 핵심 역량이다.
---
## 동적으로 문자열 처리하기
  * 1) 일괄적인 범위의 메모리를 모두 특정한 값으로 설정하기 위해서는 memset()을 사용한다.
  * 2) memset(포인터,값,크기);
  * 3) 한 바이트 씩 값을 저장하므로 문자열 배열의 처리 방식과 흡사하다.
  * 4) 따라서 memset() 함수는 <string.h> 라이브러리 안에 선언되어 있다.
---
## 정리
  * 동적 메모리 할당을 이용하면 프로그램 실행도중 메모리 공간을 배정받을 수 있다
  * 동적으로 할당받은 프로그램은 반드시 명시적으로 free()함수를 이용해 할당 해제를 해야만 한다.
  