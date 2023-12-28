### NumberGenerator
```java
public class NumberGenerator {  
    public static Integer generateRandomNumberInUnit(Integer unit) {  
        List<Integer> randomNumberList = IntStream  
                .rangeClosed(0, unit)  
                .boxed()  
                .collect(Collectors.toList());  
        return Randoms.pickNumberInList(randomNumberList);  
    }  
}
```

```java
public class NumberGenerator {  
    public static Integer pickRandomNumber(Integer minNumber,Integer maxNumber){  
        return Randoms.pickNumberInRange(minNumber,maxNumber);  
    }  
    public static Integer pickCategoryNumber(){  
        return pickRandomNumber(1,5);  
    }  
}
```