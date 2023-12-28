### OutputView

```java
public class OutputView {  
    private static OutputView INSTANCE = null;  
    private static final String ERROR_PREFIX="[ERROR] ";  
    public static OutputView getInstance() {  
        if (INSTANCE == null) {  
            INSTANCE = new OutputView();  
        }  
        return INSTANCE;  
    }  
  
    private void printNewLine() {  
        System.out.println();  
    }  
  
    public void printMessage(String message) {  
        System.out.println(message);  
    }  
    public void printErrorMessage(String errorMessage){  
        printMessage(ERROR_PREFIX+errorMessage);  
    }  
  
}
```
### OutputViewMessage
```java
public enum OutputViewMessage {  
    ;  
    private final String message;  
  
    OutputViewMessage(String message) {  
        this.message = message;  
    }  
  
    public String getMessage() {  
        return message;  
    }  
  
    public String getFormattedMessage(Object... args) {  
        return String.format(message, args);  
    }  
}
```