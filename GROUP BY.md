## GROUP BY

> 테이블에서 특정 그룹을 만들 수 있도록 하는 것이 바로 GROUP BY 절 입니다.
>
> 나누고자 하는 그룹의 컬럼명을 SELECT절과 GROUP BY절 뒤에 추가하면 된다.
>
>  집계함수와 함께 사용되는 상수는 GROUP BY 절에 추가하지 않아도 된다.



![image-20210502223556076](GROUP%20BY.assets/image-20210502223556076.png)



#### 1. 고양이와 개는 몇 마리 있을까?

동물 보호소에 들어온 동물 중 고양이와 개가 각각 몇 마리인지 조회하는 SQL문을 작성해주세요. 이때 고양이를 개보다 먼저 조회해주세요.

``` SQL
SELECT ANIMAL_TYPE, COUNT(ANIMAL_TYPE) AS COUNT
FROM ANIMAL_INS
GROUP BY ANIMAL_TYPE
ORDER BY ANIMAL_TYPE
```

![image-20210502224521543](GROUP%20BY.assets/image-20210502224521543.png)



#### 2. 동명 동물 수 찾기

동물 보호소에 들어온 동물 이름 중 두 번 이상 쓰인 이름과 해당 이름이 쓰인 횟수를 조회하는 SQL문을 작성해주세요. 이때 결과는 이름이 없는 동물은 집계에서 제외하며, 결과는 이름 순으로 조회해주세요.

``` SQL
SELECT NAME, COUNT(NAME)
FROM ANIMAL_INS
WHERE NAME is NOT NULL
GROUP BY NAME
HAVING COUNT(NAME) >= 2
ORDER BY NAME
```

![image-20210502234233054](GROUP%20BY.assets/image-20210502234233054.png)



#### 3. 입양 시각 구하기(1)

보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. 09:00부터 19:59까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요. 이때 결과는 시간대 순으로 정렬해야 합니다.

```SQL
SELECT hour, COUNT(*) count
FROM(SELECT TO_CHAR(DATETIME,'HH24') hour FROM ANIMAL_OUTS)
WHERE hour >= 9 and hour < 20
GROUP BY hour
ORDER BY hour
```

![image-20210502234031731](GROUP%20BY.assets/image-20210502234031731.png)



