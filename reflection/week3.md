이번 과제의 목표는 객체를 분리하고, 도메인 로직에 대한 단위 테스트를 작성하는 것이었습니다.

처음 목표를 마주하고 든 생각은 '어떻게 하지?'에 대한 두려움이었습니다. 
예전에 아키텍처 패턴을 공부하며 도메인 주도 설계에 대해 배웠으나, 
어려운 용어와 복잡한 구조 때문에 중간에 포기했었습니다.

그래서 , 이번에는 어렵고 복잡한 도메인 주도 설계 가 아닌 "단순히 도메인이 라는게 뭘까?" 부터 접근을 했습니다.
기존 과제들에 서도 도메인 단위로 분리를 했었지만 단순히 하나의 객체로 동작 하여 , 순서대로 작동하는 절차지향적 코드라는 생각을 벗어날 수 없었습니다.
따라서 , 한번 사용한 객체 라도 언제든지 재사용 가능하고 다른 곳에서 사용 가능하게 만들기 위해 현실의 경우를 생각하며 최대한 객체 들을 잘게 나누어 갔습니다.

결제 , 로또 구매 종이 , 로또 결과 판 , 로또 금액 판 , 통계 등 세세하게 나누어 가며 각 도메인 의 컨트롤러 에서 각각 도메인을 관리하는 식의 생각을 했으나 , 
결국 기존의 코드와 똑같이 컨트롤러가 모든 기능을 주도 하므로 해당 생각이 틀림을 깨닫고 , 
도메인이 스스로가 생성될 때 검증 및 받은 변수를 기반으로 생성이 되는식의 코드를 구현해갔습니다.

이렇게 코드를 도메인 단위로 나누면서 왜 추가 요구 사항에서 
핵심 로직 구현 코드와 UI 로직을 분리하라 하고 , UI 로직은 테스트를 제외 하라고 한지 깨달았습니다.
1,2 차시에서는 제 코드들은 도메인 단위가 아닌 , 객체의 기능 단위로 집중이 되어 있었습니다.
그렇기에 , 테스트를 할 때 다른 코드를 모킹해서 제가 의도한 값대로 나오게 해서 테스트를 할 수 밖에 없었습니다.
하지만 , 도메인 단위로 코드를 짜며 다른 함수 및 객체에 의존하지 않고 원하는 모든 테스트를 할 수 있었습니다.
로또에 대한 결과를 생성할 때도 어떤 값들이 나올 때를 의도해서 , 해당 결과를 유도하는 것이 아닌 , 
변수를 통해 도메인을 생성해서 이 값을 넣었을 때 해당 결과가 나온다로 명확하게 테스트가 가능했습니다.

그리고 , 컨트롤러는 단순 입출력 , 서비스는 도메인 간 로직 , 도메인은 자신의 연산만 수행하는 것을 깨달았습니다.
기존 백엔드 코드를 짤 때는 사실 , ORM 이 모든걸 해결해주기 때문에 도메인 부분을 어떻게 분리할지 깊게 생각하지 않았습니다.
이번에 도메인에 대해 생각하고 도메인이 수행하는 로직이 어디까지일까 대해 생각한 결과 ,
완벽하게 분리한 도메인 코드들은 다소 , 파일이 많아지고 복잡할 순 있어도 절대 SRP 원칙을 위배할 수 없다는 것 을 느꼈습니다.

마지막으로 , 이번주 코드는 더욱 추가된 요구사항 과 목표로 깊게 생각하고 리팩토링 도 자주 했던 만큼 
코드에 대한 몰입은 있어도 정답이다에 대한 확신은 없습니다. 
다른 분들의 몰입을 보며 의견을 함께 얘기하고 , 제 코드와 다른 사고방식을 보며 더 발전하고 싶다고 느꼈습니다.
