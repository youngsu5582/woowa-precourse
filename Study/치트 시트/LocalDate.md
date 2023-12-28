### LocalDate

```java
LocalDate.of(2023,12,24);
```
날짜 이 사이에 있는지 검증
```java
public boolean containPeriod(
		LocalDate startDate,
		LocalDate endDate
) {
	return !(visitDay.isBefore(startDate) || visitDay.isAfter(endDate));
}
```



### DayOfWeek
```java
DayOfWeek day = localDate.getDayOfWeek();
DayOfWee.SUNDAY
```