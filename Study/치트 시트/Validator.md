### 한글 검증

```java
private static void validateStationNameCharacter(String name) {
	if (name.chars()
			.anyMatch(character -> character < '가' || '힣' < character)) {
		throw new IllegalArgumentException(INVALID_STATION_NAME_CHARACTER.getMessage());
	}
}
```

### 첫 글자 , 끝 글자 검증
```java
private static void validateStationNameSuffix(String name) {
	if (!name.endsWith(STATION_NAME_SUFFIX)) {
		throw new IllegalArgumentException(INVALID_STATION_NAME_SUFFIX.getMessage());
	}
}
```
### 오름차순 검증
```java
IntStream.range(1, numbers.size())  
        .allMatch(i -> numbers.get(i) > numbers.get(i - 1));
```

### 쉼표 검증  
private static Pattern pattern = Pattern.compile("^([a-zA-Z가-힣]+,)*[a-zA-Z가-힣]+$");


### 마이너스 검증 (라면-3)

String regex = "^([ㄱ-ㅎㅏ-ㅣ가-힣0-9\\\\-]+,)*[ㄱ-ㅎㅏ-ㅣ가-힣0-9\\\\-]+$";

