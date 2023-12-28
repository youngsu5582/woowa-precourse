### ControllerFactory
```java
public class ControllerFactory {  
    private static GameController gameController;  
  
    public static GameController getGameController() {  
        if (gameController == null) {  
            gameController = new GameController();  
        }  
        return gameController;  
    }
}
    
```

