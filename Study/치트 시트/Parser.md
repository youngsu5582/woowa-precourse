### Parser
```java
public class Parser {  
    public static Integer parseInfoToNumber(String info) {  
        try {  
            return Integer.parseInt(info);  
        } catch (NumberFormatException exception) {  
            throw new IllegalArgumentException(ExceptionMessage.NOT_NUMBER.getMessage());  
        }  
    }  
    public static List<String> parseInfoWithSeparator(String info, String separator) {  
        return Arrays.asList(info.split(separator));  
    }  
    public static List<String> parseInfoWithSeparatorAndStrip(String info, String separator) {  
        return Arrays.stream(info.split(separator)).map(String::strip).collect(Collectors.toList());  
    }  
  
}
```
