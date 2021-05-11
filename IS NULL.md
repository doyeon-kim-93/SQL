## IS NULL

>필드 값이 비어 있는 경우 즉, NULL일때에 유무에 대한 조건이다.



![image-20210511233510243](IS%20NULL.assets/image-20210511233510243.png)



1.동물 보호소에 들어온 동물 중, 이름이 없는 채로 들어온 동물의 ID를 조회하는 SQL 문을 작성해주세요. 단, ID는 오름차순 정렬되어야 합니다.

``` SQL
SELECT ANIMAL_ID 
FROM ANIMAL_INS
WHERE NAME IS NULL
```



2.동물 보호소에 들어온 동물 중, 이름이 있는 동물의 ID를 조회하는 SQL 문을 작성해주세요. 단, ID는 오름차순 정렬되어야 합니다.

``` SQL
SELECT ANIMAL_ID 
FROM ANIMAL_INS
WHERE NAME IS NOT NULL
```



3.입양 게시판에 동물 정보를 게시하려 합니다. 동물의 생물 종, 이름, 성별 및 중성화 여부를 아이디 순으로 조회하는 SQL문을 작성해주세요. 이때 프로그래밍을 모르는 사람들은 NULL이라는 기호를 모르기 때문에, 이름이 없는 동물의 이름은 "No name"으로 표시해 주세요.

``` SQL
SELECT ANIMAL_TYPE, 
DECODE(NAME ,NULL, 'No name', NAME) NAME,
SEX_UPON_INTAKE
FROM ANIMAL_INS
ORDER BY ANIMAL_ID;
```

- SQL의 DECODE

  프로그래밍의 if else 와 같은 기능을 수행한다.

  DECODE(컬럼, 조건1, 결과1, 조건2, 결과2, 조건3, 결과3..........) 

  