# SQL

**```ANIMAL_INS```** 테이블은 동물 보호소에 들어온 동물의 정보를 담은 테이블입니다. ANIMAL_INS 테이블 구조는 다음과 같으며, ```ANIMAL_ID, ANIMAL_TYPE, DATETIME, INTAKE_CONDITION, NAME, SEX_UPON_INTAKE```는 각각 동물의 아이디, 생물 종, 보호 시작일, 보호 시작 시 상태, 이름, 성별 및 중성화 여부를 나타냅니다.

**```ANIMAL_OUTS```** 테이블은 동물 보호소에서 입양 보낸 동물의 정보를 담은 테이블입니다. ANIMAL_OUTS 테이블 구조는 다음과 같으며, ```ANIMAL_ID, ANIMAL_TYPE, DATETIME, NAME, SEX_UPON_OUTCOME```는 각각 동물의 아이디, 생물 종, 입양일, 이름, 성별 및 중성화 여부를 나타냅니다.

## SELECT 

##### 모든 레코드 조회하기
Q. 동물 보호소에 들어온 **모든 동물의 정보를 ANIMAL_ID순으로 조회**하는 SQL문을 작성해주세요.
```mysql
SELECT * FROM ANIMAL_INS ORDER BY ANIMAL_ID;
```
##### 역순 정렬하기
Q. 동물 보호소에 들어온 **모든 동물의 이름과 보호 시작일을 조회**하는 SQL문을 작성해주세요. 이때 결과는 ANIMAL_ID 역순으로 보여주세요.
```mysql
SELECT NAME, DATETIME FROM ANIMAL_INS ORDER BY ANIMAL_ID DESC;
```

##### 아픈 동물 찾기
Q. 동물 보호소에 들어온 동물 중 **아픈 동물1의 아이디와 이름을 조회**하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요.
```mysql
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION='sick';
```

##### 어린 동물 찾기
Q. 동물 보호소에 들어온 동물 중 **젊은 동물의 아이디와 이름을 조회**하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요.
```mysql
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE NOT INTAKE_CONDITION IN ('aged');
```

##### 동물의 아이디와 이름
Q. 동물 보호소에 들어온 모든 동물의 아이디와 이름을 **ANIMAL_ID순으로 조회**하는 SQL문을 작성해주세요.
```mysql
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS ORDER BY ANIMAL_ID;
```

##### 여러 기준으로 정렬하기
Q. 동물 보호소에 들어온 **모든 동물의 아이디와 이름, 보호 시작일을 이름 순으로 조회**하는 SQL문을 작성해주세요. 단, 이름이 같은 동물 중에서는 보호를 나중에 시작한 동물을 먼저 보여줘야 합니다.
```mysql
SELECT ANIMAL_ID, NAME, DATETIME FROM ANIMAL_INS ORDER BY NAME ASC, DATETIME DESC;
```

##### 상위 n개 레코드
Q. 동물 보호소에 **가장 먼저 들어온 동물의 이름을 조회**하는 SQL 문을 작성해주세요.
```mysql
SELECT NAME FROM ANIMAL_INS ORDER BY DATETIME ASC LIMIT 1;
```

## SUM, MAX, MIN

##### 최댓값 구하기
Q. **가장 최근에 들어온 동물은 언제 들어왔는지 조회**하는 SQL 문을 작성해주세요.
```mysql
SELECT DATETIME FROM ANIMAL_INS ORDER BY DATETIME DESC LIMIT 1;
```

##### 최솟값 구하기
Q. 동물 보호소에 **가장 먼저 들어온 동물은 언제 들어왔는지 조회**하는 SQL 문을 작성해주세요.
```mysql
SELECT DATETIME FROM ANIMAL_INS ORDER BY DATETIME ASC LIMIT 1;
```

##### 동물 수 구하기
Q. 동물 보호소에 동물이 몇 마리 들어왔는지 조회하는 SQL 문을 작성해주세요.
```mysql
SELECT COUNT(*) FROM ANIMAL_INS;
```

##### 중복 제거하기
Q. 동물 보호소에 들어온 동물의 이름은 몇 개인지 조회하는 SQL 문을 작성해주세요. 이때 이름이 NULL인 경우는 집계하지 않으며 중복되는 이름은 하나로 칩니다.
```mysql
SELECT COUNT(DISTINCT NAME) FROM ANIMAL_INS WHERE NAME IS NOT NULL;
```
## GROUP BY

##### 고양이와 개는 몇 마리 있을까
Q. 동물 보호소에 들어온 동물 중 고양이와 개가 각각 몇 마리인지 조회하는 SQL문을 작성해주세요. 이때 고양이가 개보다 먼저 조회해주세요.
```mysql
SELECT ANIMAL_TYPE, COUNT(*) AS COUNT FROM ANIMAL_INS GROUP BY ANIMAL_TYPE;
```

##### 동명 동물 수 찾기
Q. 동물 보호소에 들어온 동물 이름 중 두 번 이상 쓰인 이름과 해당 이름이 쓰인 횟수를 조회하는 SQL문을 작성해주세요. 이때 결과는 이름이 없는 동물은 집계에서 제외하며, 결과는 이름 순으로 조회해주세요.
```mysql
SELECT NAME, COUNT(NAME) AS COUNT_NAME 
FROM ANIMAL_INS 
WHERE NAME IS NOT NULL 
GROUP BY NAME 
HAVING COUNT_NAME >= 2;
```

##### 입양 시각 구하기(1)
Q. 보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. 9시부터 19시까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요. 이때 결과는 시간대 순으로 정렬할 것.
```mysql
SELECT SUBSTRING(DATETIME,12,2) AS HOUR, COUNT(DATETIME) AS HOUR_COUNT 
FROM ANIMAL_OUTS 
GROUP BY HOUR 
HAVING HOUR BETWEEN 9 AND 19;
```

##### 입양 시각 구하기(2)
Q. 보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. 0시부터 23시까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요. 이때 결과는 시간대 순으로 정렬할 것.
```mysql
SET @hour = -1;

SELECT @hour := @hour + 1 AS HOUR, (
    SELECT COUNT(DATETIME) 
    FROM ANIMAL_OUTS B
    WHERE HOUR(DATETIME) = @hour 
) AS COUNT FROM ANIMAL_OUTS A
WHERE @hour < 23;
```

## IS NULL 

##### 이름이 없는 동물의 아이디
Q. 동물 보호소에 들어온 동물 중, 이름이 없는 채로 들어온 동물의 ID를 조회하는 SQL 문을 작성해주세요. 단, ID는 오름차순 정렬되어야 합니다.
```mysql
SELECT ANIMAL_ID FROM ANIMAL_INS WHERE NAME IS NULL;
```

##### 이름이 있는 동물의 아이디
Q. 동물 보호소에 들어온 동물 중, 이름이 있는 동물의 ID를 조회하는 SQL 문을 작성해주세요. 단, ID는 오름차순 정렬되어야 합니다.
```mysql
SELECT ANIMAL_ID FROM ANIMAL_INS WHERE NAME IS NOT NULL;
```
