# MVVM

- MVC에서 컨트롤러가 뷰모델로 교체된 형테이고 뷰모델은 UI레이어 아래에 위치한다. 뷰모델은 뷰가 필요로 하는 데이터와 커맨드 객체를 노출해 주기 때문에 '뷰가 필요로하는 데이터와 액션을 담고 있는 컨테이너 객체'로 볼 수도 있다.

- MVVM이 MVC와 다른 점은 '뷰모델은 뷰를 지원하고 뷰가 필요한 데이터와 커맨드를 제공하기 위해서 만들어졌다'는 것이다. 이름 그대로 '뷰모델은 뷰를 위한 모델'이며 뷰모델을 뷰에 바인딩할 때 가장 강력하다. 여러가지 뷰를 제공하는 일반적인 객체가 아닌 각 뷰에 맞춰서 만들어진 것이다. 때문에 뷰는 뷰모델에 대해서만 알고 있으면 되고 그외의 아키텍처에 대해서는 신경쓰지 않아도 된다. 그래서 MVC와 가장 다른 점은 커맨드와 데이터바인딩이라고 할 수 있다. 이 2가지 요소로 인하여 뷰와 컨트롤러(MVVM에서는 뷰모델)의 관계를 끊을 수 있다. 커맨드를 사용함으로써 비헤이비어를 뷰모델에서 정의한 특정한 뷰액션과 연결할 수 있다. 데이터바인딩 특정한 뷰 속성과 뷰모델의 속성을 연결할 수 있도록 하고 뷰모델에서 속성이 변경되었을 때 뷰에 반영이 된다.

- 결국 MVP에서 중복 코드를 제거하기 위한 방법 중 하나로 생각하고 ViewModel을 사용하고 있는 형태이다. 중복 코드 줄이기, View와 Presenter의 관계 구성이 1:1을 넘어설 수 있음, ViewModel은 여러 개 만들 수 있음, 더 이상 View와 Presenter를 1:1로 가져갈 필요가 없다. 때에 따라서 ViewModel을 바라보는 View는 N 개가 될 수도 있으며, View에서도 N 개의 ViewModel을 호출해서 사용할 수 있다. 1:1관계를 벗어남과 동시에 자유로워진 ViewModel이다.

- Presenter를 분리해 내면 MVVM가 된다. 'Presenter에서 View에 대한 모델을 분리하였기 때문에 ViewModel'이다. MVVM의 기본 조건은 '종속성을 제거'하고, 'View에 대한 모델을 정의하는 것'이다. 종속성을 제거하기 위해서는 ReactiveX/Data Binding 등을 이용하는 것일 뿐이다. 그래서 MVVM은 1.종속성을 제거해야 함 2.View에 대한 Model을 분리해야 함이라는 가장 기본적인 2가지 규칙을 가지는 경우에만 저는 ViewModel이라고 정의할 수 있다. 최소한 View에 대한 Model은 정의해주어야 한다. 그렇게 해야 다음과 같은 처리가 가능해 진다. View에 대한 종속성을 줄인다-종속성을 줄이려면 ReactiveX/data-binding 등을 이용할 수 있다. View에 대한 Model 정의가 명확해야 한다-이 ViewModel은 언제든 View에서 가져다 쓰기만 하면 되고, 불필요한 경우 해당 ViewModel만 버릴 수 있어야 한다. ViewModel에 대한 테스트가 가능해진다-View에 대한 테스트와 완전하게 분리 가능하여 비즈니스 로직이 아닌 각각의 ViewModel 테스트가 가능해진다.

- ViewModel 분리가 필요할까? 분리했을 때 얻는 이점은? 종속성은? ReactiveX/Data Binding 등을 이용, 테스트 코드는? 테스트 코드는 유용해야 한다 비즈니스 로직 전체를 테스트하는 것이 아닌 하나의 ViewModel에 해당하는 비즈니스 로직의 테스트가 가능하다.

- MVVM을 사용함으로써 두 가지가 가능하다. View/Model 간의 코드 분리, 테스트 가능한 코드 작성

- MVVM은 'ViewModel과 View의 관계는 1:N 관계'이다. 이것은 View가 변하더라도 ViewModel은 재상용이 가능해야 한다는 것을 의미한다.

- ViewModel 분리 방법
    - 1개 이상의 View에서 호출하는 코드를 우선 찾아 새로운 ViewModel로 분리
    - View에서 사용하던 Presenter는 ViewModel이라는 이름으로 교체
    - ViewModel에서는 View를 들고 있지 않도록 할 수 있다. RxJava/data-binding/kotlin higher order function등을 사용해서 의존성을 줄인다. View에서 가져다 쓰면서 필요한 코드만을 구현하는 방법으로 접근한다.

참고
- https://blog.outsider.ne.kr/672
- http://thdev.tech/androiddev/2017/02/20/Android-MVP-Package-Structure.html
- http://thdev.tech/androiddev/2017/08/09/Android-MVC_MVP_MVVM-Intro.html
- http://thdev.tech/androiddev/2017/03/12/Android-MVVM-Architecture-intro.html
- http://heepie.tistory.com/221?category=730950
