
### Repository
```java
public class InfoRepository {  
    private static final List<Info> infos = new ArrayList<>();  
  
    public static List<Info> infos() {  
        return Collections.unmodifiableList(infos);  
    }  
  
    public static void addInfo(Info info) {  
        infos.add(info);  
    }  
  
  
}
```
### Domain
```java
public record Info (Line line, Section section){  

}
```

