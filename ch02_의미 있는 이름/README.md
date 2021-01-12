## 2. 의미 있는 이름
소프트웨어에서 이름은 어디나 쓰인다.  
이름을 잘 지으면 여러모로 편하다.  
이 장에서는 이름을 잘 짓는 간단한 규칙을 몇 가지 소개한다.

- ### 의도를 분명히 밝혀라
  주석이 필요하다면 의도를 분명히 드러내지 못했다는 말이다.  
  
  지뢰찾기 게임을 만드는 2 가지 코드이다.
  ```java
  public List<int[]> getThem() {
    List<int[]> list1 = new ArrayList<int[]>();
    for (int[] x : theList)
      if (x[0] == 4)
        list1.add(x);
    return list1;
  }
  ```
  ```java
  public List<int[]> getFlaggedCells() {
    List<int[]> flaggedCells = new ArrayList<int[]>();
    for (int[] cell : gameBoard)
      if (cell[STATUS_VALUE] == FLAGGED)
        flaggedCells.add(cell);
    return flaggedCells;
  }
  ```
  코드의 단순성, 연산자 수, 상수 수, 들여쓰게 단계 등이 동일한데 의미는 밑에 있는 코드가 더욱 명확하다.  
  단순히 이름만 고쳤는데도 함수가 하는 일을 이해하기 쉬워진다.
  
- ### 그릇된 정보를 피하라
  프로그래머는 코드에 그릇된 단서를 남겨서는 안 된다.
  
  - 널리 쓰이는 의미가 있는 단어를 다른 의미로 사용하면 안 된다.
  - 실제 List 타입이 아니라면 이름에 List란 단어를 하지 않는다.
  - 서로 흡사한 이름을 사용하지 않도록 주의한다.
  - 유사한 개념은 유사한 표기법을 사용한다. 일관성이 떨어지는 표기법은 그릇된 정보다.
  - `소문자 l`이나 `대문자 O` 변수는 1과 0처럼 보이므로 사용하지 않는다.
  
- ### 의미 있게 구분하라
  컴파일러를 통과할지라도 `연속된 숫자`를 덧붙이거나 `불용어(noise word)`를 추가하는 방식은 적절하지 못하다.  
  
  **연속된 숫자**  
  a1과 a2의 의미는 전혀 알 수 없다.
  
  **불용어**  
  불용어는 중복이다.  
  Name은 어차피 문자로 되어있을 테니 NameString이라 지을 필요 없다.  
  customerInfo와 customer, accountData와 account 등은 구분이 안 된다. 읽는 사람이 차이를 알도록 이름을 지어라
  
- ### 발음하기 쉬운 이름을 사용하라
  사람들은 단어에 능숙하다.  
  우리 두뇌에서 상당 부분은 단어라는 개념만 전적으로 처리한다.  
  그리고 정의상으로 단어는 발음이 가능하다.  
  말을 처리하려고 발달한 두뇌를 활용해야 하므로 발음하기 쉬운 이름을 선택한다.
  
  발음하기 힘든 genymdhms말고 발음하기 쉬운 generationTimestamp를 사용해라.
  
- ### 검색하기 쉬운 이름을 사용하라
  문자 하나를 사용하는 이름과 상수는 텍스트 코드에서 쉽게 눈에 띄지 않는다.  
  MAX_CLASSES_PER_STUDENT는 검색으로 찾기 쉽지만, 숫자 7은 은근히 까다롭다.  
  7이 들어가는 파일 이름이나 수식이 모두 검색되기 때문이다.
  
  간단한 메서드에서 로컬 변수만 한 문자를 사용한다.  
  **이름 길이는 범위 크기에 비례해야 한다.**  
  
- ### 자신의 기억력을 자랑하지 마라
  독자가 코드를 읽으면서 변수 이름을 자신이 아는 이름으로 변환해야 한다면 그 변수 이름은 바람직하지 못하다.  
  이는 일반적으로 `문제 영역`이나 `해법 영역`에서 사용하지 않는 이름을 선택했기 때문에 생기는 문제다.
  
  루프에서 반복 횟수를 세는 변수 i, j, k는 괜찮다. `(l은 절대 안 된다!)`  
  단, 루프 범위가 아주 작고 다른 이름과 충돌하지 않을 때만 괜찮다.  
  루프에서 반복 횟수 변수는 전통적으로 한 글자를 사용하기 때문이다. 그 외에는 대부분 적절하지 못하다.
  
- ### 클래스 이름
  클래스 이름과 객체 이름은 명사나 명사구가 적합하다.  
  Manager, Processor, Data, Info 등과 같은 단어는 피하고, 동사는 사용하지 않는다.
  
- ### 메서드 이름
  메서드 이름은 동사나 동사구가 적합하다.  
  접근자, 변경자, 조건자는 javabean 표준에 따라 값 앞에 get, set, is를 붙인다.
  ```java
  String name = employee.getName();
  customer,setName("mike");
  if (paycheck.isPosted())...
  ```
  생성자를 오버로딩할 때는 정적 팩토리 메서드를 사용한다.
  ```java
  Complex fulcrumPoint = Complex.FromRealNumber(23.0);
  ```
  
- ### 기발한 이름은 피하라
  재미난 이름보다 명료한 이름을 선택해라.  
  의도를 분명하고 솔직하게 표현해라.
  
- ### 한 개념에 한 단어를 사용하라
  똑같은 메서드를 클래스마다 fetch, retrieve, get으로 제각각 부르면 혼란스럽다.  
  어느 클래스에서 어느 이름을 썼는지 기억하기 어렵다.  
  메서드 이름은 독자적이고 일관적이어야 한다.
  
- ### 말장난을 하지 마라
  한 단어를 두 가지 목적으로 사용하지 마라.  
  다른 개념에 같은 단어를 사용한다면 그것은 말장난에 불과하다.
  
  값 두개를 더하거나 이어서 새로운 값을 만드는 기능을 하는 메서드를 add로 사용했으면 집합에 값 하나를 추가하는 메서드를 만들 때 add라 하지 마라.  
  기존 add 메서드와 맥락이 다르다. insert나 append라는 이름이 적당하다.
  
- ### 해당 역역에서 가져온 이름을 사용하라
  코드를 읽은 사람도 프로그래머라는 사실을 명심한다.  
  그러므로 전산 용어, 알고리즘 이름, 패턴 이름, 수학 용어 등을 사용해도 괜찮다.  
  모든 이름을 문제 영역에서 가져오는 정책은 현명하지 못하다.  
  기술 개념에는 기술 이름이 가장 적합한 선택이다.
  
- ### 문제 영역에서 가져온 이름을 사용하라
  적절한 프로그래머 용어가 없다면 문제 영역에서 이름을 가져온다.  
  문제 영역 개념과 관련이 깊은 코드라면 문제 영역에서 이름을 가져와야 한다.
  
  우수한 프로그래머와 설계자라면 해법 영역과 문제 영역을 구분할 줄 알아야 한다.
  
- ### 의미 있는 맥락을 추가하라
  스스로 의미가 분명한 이름이 있긴 하지만 대다수 이름은 그렇지 못하다.  
  그래서 클래스, 함수, 이름 공간에 넣어 맥락을 부여한다.
  
  맥락이 불분명한 변수와 맥락이 분명한 변수의 차이를 나타내는 2 가지 코드를 살펴보자.
  
  ```java
  private void printGuessStatistics(char candidate, int count) {
    String number;
    String verb;
    String pluralModifier;
    
    if (count == 0) {
      number = "no";
      verb = "are";
      pluralModifier = "s";
    } else if (count == 1) {
      number = "1";
      verb = "is";
      pluralModifier = "";
    } else {
      number = "Integer.toString(count)";
      verb = "are";
      pluralModifier = "s";
    }
    
    String guessMessage = String.format(
      "There %s %s %s%s", verb, number, candidate, pluralModifier
    );
    
    print(guessMessage);
  }
  ```
  ```java
  public class GuessStatisticsMessage {
    private String number;
    private String verb;
    private String pluralModifier;
    
    public String make(char candidate, int count) {
      createPluralDependentMessageParts(count);
      return String.format(
        "There %s %s %s%s",
        verb, number, candidate, pluralModifier );
    }
    
    private void createPluralDependentMessageParts(int count) {
      if (count == 0) {
        thereAreNoLetters();
      } else if (count == 1) {
        thereIsOneLetter();
      } else {
        thereAreManyLetters(count);
      }
    }
    
    private void thereAreManyLetters(int count) {
      number = "Integer.toString(count)";
      verb = "are";
      pluralModifier = "s";
    }
    
    private void thereIsOneLetter() {
      number = "1";
      verb = "is";
      pluralModifier = "";
    }
    
    private void thereAreNoLetters() {
      number = "no";
      verb = "are";
      pluralModifier = "s";
    }
  }
  ```
  전자는 함수를 끝까지 읽어보고 나서야 number, verb, pluralModifier라는 변수 세 개가 통계 추측 메시지에 사용된다는 사실이 드러난다.  
  후자는 세 변수를 함수 전반에서 사용한다. 그리고 변수를 클래스 안에서 사용하므로 맥락이 분명해진다.
  
- ### 불필요한 맥락을 없애라
  accountAddress와 customerAddress는 Address 클래스 인스턴스로는 좋은 이름이나 클래스 이름으로는 적합하지 못하다.  
  Address는 클래스 이름으로 적합하다. 의미가 분명한 경우에 한해서 일반적으로 짧은 이름이 긴 이름보다 좋다.
