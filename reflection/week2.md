이번 과제에서는 과제의 목표와 1주차 피드백을 지키면서 구현하려고 했습니다.  
그러한 이유로는 피드백 과 과제 목표에서 제게 인상 깊게 다가 왔던 부분들이 있었기 때문입니다.  

피드백에서 인상 깊은 부분은 이름을 축약 하지 말라는 것 과 의미 없는 주석을 달지 않는다는 내용 이였습니다.

어느 순간 백엔드 코드를 짜면서 이름을 생각하기 귀찮아서 , 혼자서 구현하는 시간이 길어지다 보니 , 
변수명 이나 함수명도 제 스스로 알기 쉬운 이름으로 하고 , 그냥 JSDoc 이나 Javadoc 이나 Swagger 로 설명 하면 되겠지 라는 안일함 에 빠져 있음 을 깨달았습니다.

그렇기에 , 코드 구현 보다는 함수 와 변수 명을 정하는 것에 최선을 다했던 거 같습니다.
혼자만 이름을 생각한 기존의 딜레마를 벗어나기 위해 프리코스를 하지 않는 사람에게 함수명 만 보고 무슨 기능을 할 지 유추해보라 하고 , GPT 새로운 채팅을 반복하며 몰입했습니다.

몰입하며 느낀점은 꼭 긴 이름일 필요도 , 이름에 설명이 많을 필요도 없다는 것을 느낀거 같습니다.
예시로 , 차가 임계점을 넘으면 앞으로 나아가는 함수명을 처음에는 단순히 길고 전부 표현하는게 좋다고 생각해  
checkCanMoveForwardIfSpeedIsExceedThreshold 라는 무지막지하게 길고 오히려 이해를 힘들게 하는 함수명을 생각했었습니다.
하지만 , 이게 최선일까 생각하며 고민하다가 checkCarSpeedIsExceedThreshold 라는 함수명으로 수정했습니다.

목표에서 인상 깊은 부분은 함수 분리에 익숙해지라는 부분 이였습니다.

복잡한 코드를 구현 하면서 함수 하나가 다양한 기능을 하는 것은 어쩔수 없다고 생각했었습니다.
테스트 코드를 짜면서 이게 정말 이 함수를 테스트 하는 테스트가 맞는지 의구심이 들은게 이런 부분 때문임 을 깨달았습니다.
특히 , 기존에는 전부다 protected 나 public 접근자로 선언하고 , 테스트 코드에서 다른 클래스들의 함수를 모킹 한게 테스트 코드를 대충 짠 지에 대해서 느꼈습니다.
이번 기회에 SRP 원칙을 준수하고 , 접근 제한자를 다 private 로 선언하여 , 외부에서 접근은 못하고 ,  모든 케이스에 대해 테스트를 짜려고 최선을 다했습니다.

이런 과정중 인상깊은 점은 Randoms 클래스 모킹 이였던거 같습니다.
모킹을 고민하게 된 이유로는 ,
첫 번째로 1주차에도 똑같은 시도를 하다 막혀서 이번에는 반드시 해보겠다는 오기 때문 이였습니다.
두 번째로 해당 클래스를 모킹해야만 내부 함수 및 변수에 접근하지 않고도 결과를 의도 할 수 있었기 때문입니다.

단순히 , 그냥 모킹하면 될 거라고 생각했지만 해당 함수는 static 으로 , 
일반적인 모킹한 결과 gradlew 를 사용한 전체 테스트를 수행할 때 재사용 문제로 인해 에러가 떴습니다.
그래서 , 원할때만 , 함수가 의도한 값을 호출하게 하고 싶었습니다.

우선 , ApplicationTest 에서 사용하는 코드를 찾아보았습니다. 
해당 코드에서는 Executable 이라는 Java 를 공부하지 않은 저에게는 첨보는 클래스가 있었습니다.
그래서 , 우선 해당 클래스에 대해 간단히 공부하고 이게 실행을 하는 함수인 Javascript 에서 익명함수와 유사하다는 것을 깨달았습니다.
assertRandomTest 를 보며 , 제가 사용해야 하는 부분임을 깨닫고 이를 통해 항상 임계값보다 작은 값 , 큰 값이 나오는 함수를 만들었습니다.

테스트 코드를 짜며 느낀점은 SRP 가 테스트에 매우 접목이 되어 있다는 것을 느꼈습니다.
함수가 여러 기능을 하면 할 수록 , 테스트가 기존의 코드가 아닌 편법적 으로 짤 수 밖에 없기 때문입니다.

다음 주차에도 , 피드백 과 과제의 목표를 지키기 위해 최선을 다하지만 기존의 목표들을 잊지 않고 꾸준히 쌓아가며 구현을 해나갈 거 같습니다.