### CustomException
```java
public class CustomException extends IllegalArgumentException{  
    private static String ERROR_MESSAGE_PREFIX = "[ERROR] ";  
    public CustomException(String message) {  
        super(ERROR_MESSAGE_PREFIX + message);  
    }  
    public CustomException(String message,Exception exception) {  
        super(ERROR_MESSAGE_PREFIX + message,exception);  
    }  
}
```

### ExampleException
```java
public class CoinException extends CustomException {  
    public CoinException(CoinExceptionMessage errorMessage) {  
        super(errorMessage.getMessage());  
    }  
  
    public CoinException(CoinExceptionMessage errorMessage, Exception exception) {  
        super(errorMessage.getMessage(), exception);  
    }  
  
}
```
### ExampleExceptionMessage
```java  
public enum ExceptionMessage {  
INVALID_GAME_COMMAND("올바르지 않은 커맨드입니다."); 
    private final String message;  
  
    ExceptionMessage(String message) {  
        this.message = message;  
    }  
  
    public String getMessage() {  
        return message;  
    }  
  
}
```