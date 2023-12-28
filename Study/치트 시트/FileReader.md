```java
import java.io.BufferedReader;  
import java.io.FileReader;  
import java.io.IOException;  
import java.util.ArrayList;  
import java.util.List;

public class FileReaderUtil {  
    public static List<String> readData(String filePath) {  
        try (BufferedReader reader = new BufferedReader(new FileReader(filePath))) {  
            String line;  
            List<String> readData = new ArrayList<>();  
            while ((line = reader.readLine()) != null) {  
                readData.add(line);  
            }  
            return readData;  
        } catch (IOException e) {  
            e.printStackTrace();  
        }  
        return null;  
    }  
}
```
