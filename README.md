# JDD (Ju-Dung-A-Li Driven Development/주둥아리 주도 개발)
![image](https://user-images.githubusercontent.com/10369528/130068355-049861db-ce6e-45cd-a74c-a262ee4fb01a.png)

JDD는 코드 작성보다 변명거리를 우선 생각하는 개발 방법론이다. 이 방법론은 수많은 버그를 양산할 수 있다.

JDD는 아래와 같은 중요 가치를 따른다.

우리는

- 남이 쓰는 기술보다는 내 것을
- Clean한 코드보다는 Tricky한 것을
- 버그 Fix보다는 변명을
- 귀찮음보다는 편함을

훨씬 가치있게 여긴다. 이 말은, 개발자에게 지금 당장 편해보이는 것에 더 높은 가치를 둔다는 것이다.

JDD를 실천하기 위해서는 주위의 비난과 갈굼을 수없이 듣는 험난한 길일지라도 쉬지 않고 꾸준하게 노력해야 한다.
중요한 것은 이슈와 관련된 힙한 용어를 들먹이면서 실제 문제에 대한 답변을 최대한 회피하는 것이다. 이는 꾸준한 연습이 필요하다.


# JDD를 위한 지침서

## JDD를 위한 소양

JDD의 기초가 되는 소양을 항상 명심하자.

### 참된 리더
참된 리더는 부하 직원을 괴롭히지 않는다.

- 누군가 PR을 했다는 사실 자체가 보기 좋은 일이다. LGTM(Looks Good To Me).
- 누군가 PR을 날리면 자동으로 LGTM을 날리는 CI/CD를 활용해라. 반짝이는 따봉 아이콘은 보는 이의 기분을 즐겁게 한다.

### 방어적 프로그래밍
방어적 프로그래밍은 개발자의 기본 소양이다.

- 방어적 프로그래밍을 해라. 단, 코드로 방어하지 말고 너에게 들어오는 일감을 방어해라.
- 작업할 양이 많은가? 그냥 특정 테스트 케이스에서만 돌아가게 짜고 나머지는 "고도화" 작업에서 한다고 해라. 그리고 "고도화" 작업을 하기 전에 얼른 이직하자. 이직은 연봉을 올리기에도 좋은 수단이다.

## 성과 위주 회피
일 잘하는 척 편안한 생활을 위해 성과 위주로 행동해야 한다. 짤리기는 싫으니까!

### 동시성 및 병렬성
동시성이나 병렬성은 어렵고, 성과가 눈에 띄지 않는다.

- 멀티 쓰레드 환경에서 가변변수 사용으로 인한 오류는 가끔 발생한다.
가끔 발생한다는 것에 비하여 사용은 너무 편하다. 누가 뭐라고 하면 확률적으로 웬만해서는 그럴 일 없다고 하면 그만이다.
- 어쩔 수 없이 멀티 쓰레드 업무가 들어오면, 언어를 욕하면서 이 작업이 왜 어려운지 설명해라.
아 이 언어는 Actor 모델이 빈약해서요, CSP(Communicating Sequential Processes) 구현체가 없어서요, STM(Software Transactional Memory)이 지원 안 되어서요. 욕을 할수록 작업 기한이 늘어난다.
- 언어나 라이브러리, 프레임워크 수준에서 제공하는 고차원적인 동시성/병렬성 추상화는 피한다. 아 진짜 사나이라면 로우레벨을 만져야지 어딜 계집애처럼 덕지덕지 추상화된 것을 만지려 하는가?
- 비동기 흐름 내에서 동기 함수를 몰래 써도 된다. 솔직히 동기적인 함수가 프로그래밍할 때는 훨씬 편하지 않은가? 여기에 운이 좋으면 병목 찾는 작업 + 비동기로 개선하는 작업하는 기한까지 나중에 받을 수 있다.

### 문서화
우리의 본분을 잊지 말자. **꿀을 빠는 것!**

- 주석은 절대 작성하지 않는다. 누가 뭐라고 하면 클린코드를 들먹이자. 물론 그렇다고 해서 코드가 리더블하지는 않다.
- 반대로 모든 것을 주석으로 해치울 수도 있다. 코드 한 줄에 주석 한 줄이면 마땅히 "주석 주도 프로그래밍"이라 할 수도 있을 것이다. 여기서 중요한 건, 처음에 한번 빡세게 정성을 들인 뒤에는 주석에 전혀 신경쓰지 않는 것이다.
- 우리는 개발자다. 어떠한 이유에서든지 문서 작성은 금물. 누가 뭐라고 하면 "코드가 곧 문서"라고 하자.

## 뭐든 프로그래밍

세상은 0과 1로 이루어졌다고 할 수 있다. 그러니까 뭘 하든지 내가 하는 것은 프로그래밍인 것이다.

### 모던 프로그래밍
모던(Modern)은 현재이다. 즉, 지금 내가 쓰는 기술이 곧 모던한 기술이라 할 수 있다.

- 예외 처리를 하지 않는다. 누가 뭐라고 하면 Let it crash 전략이라고 한다. 예외 처리 따위는 Stack Unwinding 같은 비싼 비용이 드는 작업일 뿐이다.
- 언어의 Feature를 최대한 사용하지 않는다. 누가 뭐라고 하면 유지보수를 위해 누구나 알 수 있게 짜둔 거라고 한다. `foreach` 대신 고전적인 `for`문을 사용하는 것이 아마 성능에도 유리할 것이다. 너무나 당연한 것이니 검증해볼 필요는 없다.
- 언어의 Feature를 최대한 활용하자. 누가 뭐라고 하면 모던 프로그래밍이라고 하면 된다. 이걸 알아보지 못하는 팀원은 그 사람이 뒤떨어지는 것이니 가볍게 무시해주자.
- 의존성이 복잡하게 연결되어 있으면 디자인 패턴이라고 하자. 누가 따지면 "아니 어떻게 프로그래머가 GoF의 23가지 디자인 패턴도 모를 수가 있어요?"라고 반격하자.
- 체이닝(Chaining)이 하나라도 있으면 Fluent API 스타일이라고 하자.
- 체이닝이 하나도 없으면 디미터의 법칙을 준수한 것이라고 하자. 내가 이렇게 객체지향 원칙을 달달 외우고 있다고 자랑할 수 있는 것은 덤이다.
- 함수들만 호출하는 함수가 있으면, 미니 언어로 DSL을 구축했다고 해라.
- 데이터를 넘겨주는 함수가 있으면, Data-Driven Programming이라고 해라.
- 함수 파라미터가 너무 많아졌다? 누가 뭐라고 하면 보다 "순수"하게 짠 거라고 해라. 함수 안에서 부작용이 일어나든 말든 상관할 필요 없다.
- 람다 함수로만 구성한다. 누가 뭐라고 하면 함수를 보다 적극적으로 일급으로 다루는 함수형 프로그래밍이라고 한다.
- 디자인 패턴을 전혀 쓰지 않는다. 누가 뭐라고 하면 단순성의 원칙이라고 한다. Keep it simple, Stupid!
- Map-Reduce-Filter 같은 고차함수는 일절 사용하지 않는다. 누가 뭐라고 하면 이 역시 단순성의 원칙이라고 하자.
- 어노테이션과 같은 메타데이터를 수십개는 달자. 누가 뭐라고 하면 메타 프로그래밍 기법이라고 한다.
- OOP(Object-Oriented Programming)로 개발하는 사람들 사이에서 FP(Functional Programming)에서 통용되는 패턴을 적극 활용하자.
라이브러리까지 가져다 쓰면 더 좋다. `Maybe` 클래스를 만드는건 기본 중의 기본. 누가 뭐라고 하면 "이게 요즘 스타일이예요"라고 하자.
- FP로 개발하는 사람들 사이에서 OOP의 패턴과 가변 변수를 적극 활용하자. 누가 뭐라고 하면, "이렇게 하는게 더 편한데요?"라고 하자.
- 콜백  지옥을 보고 누가 이거 뭐냐고 물어보면, 예로부터 내려오는 전통적인 CPS(Continous Passing Style)라고 답해줘라. 틀린 말도 아니지 않은가.
- 모든 if문은 삼항 연산자로만 써라. 누가 뭐라고 하면, "아 if는 문이고 삼항은 식이니까요"라고 하자.
- 리스트 컴프리헨션, 옵셔널 체이닝, 리액티브 등을 잔뜩 쓰고 자랑스럽게 말해라. "모나딕하게 해결했다"고. 그게 뭐냐고 물어보면 "모나드의 저주로 인하여 설명하기 힘들다"까지 말해줘야 한다.
- 두 개 이상 실행되는 서비스가 있으면 어쨌든 요즘 유행하는 MSA(Micro-Service Architecture)다. 테스트를 돌려주는 스크립트만 따로 있어도 MSA다. 거기에 언어가 다르면 폴리글랏(polyglot)이니 금상첨화다.

### 설계
어떻게 설계해도 아무튼 돌아간다.

- 클래스, 인터페이스, 이넘, 멤버 등 구조 설계에 대해서 뭐라고 하면, ADT(Abstract Data Tree)에서 합타입이 어쩌고 곱타입이 어쩌고 하는 복잡한 용어를 들먹이자.
- 클래스에 기능이 너무 적으면, "아 그건 레코드로 쓰려고 했습니다."라고 하자. 그렇다고 해서 최신 언어 사양에 도입된 Record 타입을 쓰지는 말자. 기존 프로젝트에서의 호환성을 생각해야 할 것 아닌가?
- 상속이 합성보다 편하다. 누가 뭐라고 하면, OOP에서는 당연히 상속을 써야 하는게 맞다고 하면 된다. 쓰면 안 될 기능이라면 왜 언어에 들어갔겠는가?
- `null`은 10억 달러의 가치가 있다. 뭐든 애매하면 `null`을 리턴해라. 그것 때문에 문제가 생겼다면, 그건 그걸 받아가서 `null` 체크도 안 한 바보 녀석이 책임질 일이다.
- `Object`나 `Any`는 다형성(Polymorphism)의 극의이다. 뭐든 애매하면 `Object` 타입으로 반환하라. 가능하면 `Object` 타입을 리턴하는 함수에서 `null`을 반환하도록 하는 것이 가장 좋다.

### 테스트
솔직히 테스트 코드 짜는 건 재미 없고 시간만 잡아먹는다. 그거 짜면 일정에 여유가 절로 생기나?

- 테스트 코드를 전혀 작성하지 않는다. 누가 뭐라고 하면 대화형 환경(repl.it이나 크롬 개발자 도구)로 수동 테스트를 손수 했다고 하자.
- 테스트가 어떨 때는 성공하고 어떨 때는 실패하면, "속성 기반 테스트"를 작성해서 그렇다고 해라.

### 성능 최적화
CPU 성능은 내 실력과 달리 날로 발전한다. 메모리나 저장장치 용량도 마찬가지로 쭉쭉 늘어나고 있다.

- DTO/VO 변환은 쓰지 않는다. 누가 뭐라고 하면 성능 최적화라고 해라. 객체 하나 만드는 데 CPU 자원과 메모리 용량이 얼마나 드는데!
- 데이터베이스에는 필요한 필드를 그때그때 추가해라. 정규화나 규칙은 생각조차 하지 말아라. 누가 뭐라고 해도 이 또한 성능 최적화이다. 역정규화를 들먹이면 아마 양해해줄 것이다.
- 패턴이나 아키텍처는 쓰지 않는다. 클래스로도 나누지 마라. N중 for문과 if문으로 절차적으로 작성해라.
누가 뭐라고 하면 이건 진짜 성능 최적화라고 해라. 컴파일러의 최적화 따위 손으로 직접 쓴 절차적 코드를 이길 수 있을 리가 없다.
- 성능 최적화는 그 어떠한 경우에도 금물. 누가 뭐라고 하면 요즘은 "컴파일러" 한테 맡기는게 대세라고 해라. 사람이 직접 최적화에 신경쓸 수 있을 정도로 프로그래머는 한가하지 않은 법이다.

## 휴먼 오토메이션(Human Automation)

### 백엔드
백앤드는 모던 비즈니스의 핵심이다. 엄한 데서 힘빼지 말자.

- 그건 DBA가 해야 할 일이라고 해라.
- 그건 DevOps 엔지니어가 해야 할 일이라고 해라.
- 그건 프론트엔드가 해야 할 일이라고 해라.
- 그건 기획팀에서 먼저 기획해야 할 일이라고 해라.
- 그건 운영팀에게서 먼저 확인받아야 할 일이라고 해라.

### 프론트엔드
프론트엔드는 유저가 마주하는 첫인상이다. 엄한 데서 힘빼지 말자.

- 그건 백엔드가 해야 할 일이라고 해라.
- 그건 앱 개발자가 해야할 일이라고 해라.
- 그건 퍼블리셔가 해야 할 일이라고 해라.
- 그건 디자이너가 해야 할 일이라고 해라.
- 그건 유저가 해야 할 일이라고 해라.

## 기타
솔직히 좀 뇌절인듯?

- 그 날 배운 기술은 잊기 전에 즉시 회사 프로젝트에 적용해라. 누가 뭐라고 하면 그 날 배운 지식을 자랑하면 된다. 배운 것은 직접 써봐야 기억에 남을 것이 아닌가?
- 기술 스택을 공부하지 말고, 해당 기술 스택의 단점만 검색해라. 누가 해당 기술 스택을 물어보면, 기억하고 있던 단점만 들먹이자.
- CI/CD는 사용하지 말아라. 개발자의 손수 정성이 들어가지 않은 빌드를 내놓는 것이 부끄럽지도 않은가?
- Docker같이 가상화가 조금이라도 들어간 것은 사용하지 말아라. 누가 뭐라고 하면 네이티브 환경에서의 확인이 필요하다고 해라. 컨테이너 기술과 가상화의 차이점 따위 알 게 뭔가? 내가 보기에는 아무튼 그게 그 밥에 그 나물이다.
- Infrastructure as a Code 같은 것은 믿을 수 없다. 보이지 않는 뒷단에서 무슨 코드가 어떻게 실행되었을지 믿고 쓸 수 있단 말인가? 차가운 기계를 믿느니 인간의 감성어린 손길을 믿어야 한다.

# Reference
놀랍게도 꽤 많이 참고했다
- [유지보수하기 어렵게 코딩하는 방법: 평생 개발자로 먹고 살 수 있다](https://www.hanbit.co.kr/store/books/look.php?p_code=E2375873090)
- [애자일 선언](https://agilemanifesto.org/iso/ko/manifesto.html)
- [프로그래밍의 정석](http://www.yes24.com/Product/Goods/55254076)
- [7가지 동시성 모델](http://www.yes24.com/Product/Goods/29331038)
- [폴리글랏 프로그래밍](http://www.yes24.com/Product/Goods/12204890)
- [클린 코드](http://www.yes24.com/Product/Goods/11681152)
- [클린 아키텍쳐](http://www.yes24.com/Product/Goods/77283734)
- [클로저 프로그래밍의 즐거움](http://www.yes24.com/Product/Goods/24555451)
- [프로그래밍 스칼라](http://www.yes24.com/Product/Goods/27767797)
- [FSharp Fun and Profit 블로그](https://fsharpforfunandprofit.com/)
- [로버트 C 마틴 블로그](https://blog.cleancoder.com/)
- [마틴 파울러 블로그](https://martinfowler.com/)
- 그외 언젠가 한번쯤 읽어본 책들 다수

# Contributing
더 좋은 주둥아리 방법을 알고 있다면 PR을 날려주세요

# License
JDD는 어떠한 제약조건도 없습니다.
단, 이걸 실천했을 때의 결과에 관하여 어떤 책임도 지지 않습니다.
