# SQL

## WITH NAME AS ()
```SQL
WITH NAME AS (
    SELECT  ...
    FROM    ...
)
SELECT  ...
FROM    NAME, ...   -- 여기서 WITH에 선언한 NAME 사용 가능
```


## CONNECT BY
```sql
-- SELECT  LPAD(LEVEL - 1, 2, '0') HOUR 
SELECT  LEVEL -- 1, 2, 3, 4, 5
FROM    dual 
CONNECT BY LEVEL <=5;
```

### LPAD 함수
지정한 길이 만큼 왼쪽부터 특정문자로 채우기<br>
LPAD(값, 문자길이, 빈자리 채울 문자)<br>

### RPAD 함수
지정한 길이 만큼 오른쪽부터 특정문자로 채우기<br>
RPAD(값, 문자길이, 빈자리 채울 문자)<br>