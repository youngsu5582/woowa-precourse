### InputView
```java
public class InputView {  
    private static InputView INSTANCE=null;  
    public static InputView getInstance(){  
        if(INSTANCE==null){  
            INSTANCE = new InputView();  
        }  
        return INSTANCE;  
    }  
    public String readInput(){  
        return Console.readLine();  
    }  
    public String inputCommand(){  
      
    return readInput();  
}
}
```
### InputViewMessage
```java
public enum InputViewMessage {  
    ;  
    private final String message;  
  
    InputViewMessage(String message) {  
        this.message = message;  
    }  
  
    public String getMessage() {  
        return message;  
    }  
    
}
```