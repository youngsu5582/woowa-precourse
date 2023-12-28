# Format 형식 맞추기 형식 Formatting

## [](https://github.com/gitchannn/studeeeeeeee/blob/main/out/production/woowa-eunkeeee/SPEEDY.md#resultformatter)ResultFormatter

- 결과값을 출력하는 과정이 복잡할 때
- 결과값을 formatting하는 일을 model이 하는 것은 부적절, view에서 하기에도 클 수 있다.

### [](https://github.com/gitchannn/studeeeeeeee/blob/main/out/production/woowa-eunkeeee/SPEEDY.md#%ED%81%B0-%EC%88%AB%EC%9E%90-%EB%8B%A4%EB%A3%A8%EA%B8%B0-bigdecimal)큰 숫자 다루기 `BigDecimal`

- 소수점, 반올림을 빡세게 요구할 때
    
- 너무 복잡한 수나, 아니면 돈을 다루는 경우에 바로 사용하자!
    
- 퍼센트를 구한 다음에 `1,000.3%` 꼴로 출력하자
    
- `ArithmeticException`을 조심하자!
    
- dividend, divisor, quotient [![img.png](https://github.com/gitchannn/studeeeeeeee/raw/main/out/production/woowa-eunkeeee/img.png)](https://github.com/gitchannn/studeeeeeeee/blob/main/out/production/woowa-eunkeeee/img.png)
    
- 소수점 아래 둘째 자리에서 반올림 `1.35 => 1.4`
    

```
    private static BigDecimal getSetScale(BigDecimal rewardRate) {
        return rewardRate.setScale(1, RoundingMode.HALF_EVEN);
    }
```

- 퍼센트 구하기 `totalCashPrize / ticketBudget * 100` + 소수점 아래 둘째 자리에서 반올림

```
 private static BigDecimal calculatePercent(BigDecimal totalCashPrize, BigDecimal ticketBudget) {
        if (ticketBudget.equals(BigDecimal.ZERO)) {
            return BigDecimal.ZERO;
        }
        return totalCashPrize.multiply(new BigDecimal("100")).divide(ticketBudget, 1, RoundingMode.HALF_EVEN);
    }
```

- 이외의 `REGEX`를 활용한 `formatting`

```
   private enum Regex {
        CASH_PRIZE_REGEX("\\B(?=(\\d{3})+(?!\\d))"), 
        DECIMAL_FORMAT("#,##0.0");

        private final String regex;

        Regex(String regex) {
            this.regex = regex;
        }
    }

    // 12345 => 12,345
    public static String formatRewardRate(BigDecimal rewardRate) {
        return new DecimalFormat(Regex.DECIMAL_FORMAT.regex).format(rewardRate);
    }

    // 324329209.35823 => 324,329,209.4
    private static String formatCashPrize(int cashPrize) {
        return String.valueOf(cashPrize).replaceAll(Regex.CASH_PRIZE_REGEX.regex, ",");
    }
```

### [](https://github.com/gitchannn/studeeeeeeee/blob/main/out/production/woowa-eunkeeee/SPEEDY.md#enum-%ED%81%B4%EB%9E%98%EC%8A%A4-%EA%B4%80%EB%A6%AC)Enum 클래스 관리

#### [](https://github.com/gitchannn/studeeeeeeee/blob/main/out/production/woowa-eunkeeee/SPEEDY.md#command-%EA%B4%80%EB%A6%AC-%EC%82%AC%EC%9A%A9%EC%9E%90%EA%B0%80-%EC%9E%85%EB%A0%A5%ED%95%9C-%EC%98%B5%EC%85%98)Command 관리!!! (사용자가 입력한 옵션)

```
public enum MainOption {
    PAIR_MATCHING("1"),
    PAIR_SEARCHING("2"),
    PAIR_INITIALIZING("3"),
    QUIT("Q");

    private final String command;

    MainOption(String command) {
        this.command = command;
    }

    public static MainOption from(String command) {
        return Arrays.stream(MainOption.values())
                .filter(option -> option.command.equals(command))
                .findAny()
                .orElseThrow(() -> new IllegalArgumentException(ExceptionMessage.NO_MAIN_OPTION.getMessage()));
    }
    
    // NO_MAIN_OPTION => "해당하는 메인 옵션이 존재하지 않습니다."

    public boolean continueMain() {
        return this != QUIT;
    }

}
```

### Result Formatter

``` java
  private enum Regex {
        CASH_PRIZE_REGEX("\\B(?=(\\d{3})+(?!\\d))"),
        DECIMAL_FORMAT("#,##0.0");

        private final String regex;

        Regex(String regex) {
            this.regex = regex;
        }
    }

    // 12345 => 12,345
    public static String formatRewardRate(BigDecimal rewardRate) {
        return new DecimalFormat(Regex.DECIMAL_FORMAT.regex).format(rewardRate);
    }

    // 324329209.35823 => 324,329,209.4
    private static String formatCashPrize(int cashPrize) {
        return String.valueOf(cashPrize).replaceAll(Regex.CASH_PRIZE_REGEX.regex, ",");
    }
```