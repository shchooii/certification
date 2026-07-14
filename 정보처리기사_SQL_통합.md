# 정보처리기사 실기 · SQL 통합 문제

- 수록 범위: 2022년 3회 ~ 2026년 1회 (+ 2020년 1회 ~ 2022년 2회 선별 수록)
- 총 문제 수: 26문제
- SQL문 작성, SQL 실행 결과, SELECT·JOIN·집계·서브쿼리 등의 문제를 포함합니다.
- 관계대수와 데이터베이스 용어 문제는 이론(용어) 파일에 수록했습니다.

---

## 2022년 3회 · 문제 7

- 출처: `2022년_3회.md`
- 분류: SQL

다음과 같이 테이블을 정의하고 튜플을 삽입하였을 때 각 번호(①, ②)의 SQL문을 실행한 결과를 쓰시오.

```sql
CREATE TABLE 부서 (
    부서코드 INT PRIMARY KEY,
    부서명 VARCHAR(20)
);

CREATE TABLE 직원 (
    직원코드 INT PRIMARY KEY,
    부서코드 INT,
    직원명 VARCHAR(20),
    FOREIGN KEY (부서코드) REFERENCES 부서 (부서코드)
        ON DELETE CASCADE
);

INSERT INTO 부서 VALUES(10, '영업부');
INSERT INTO 부서 VALUES(20, '기획부');
INSERT INTO 부서 VALUES(30, '개발부');

INSERT INTO 직원 VALUES(1001, 10, '이진수');
INSERT INTO 직원 VALUES(1002, 10, '곽연경');
INSERT INTO 직원 VALUES(1003, 20, '김선길');
INSERT INTO 직원 VALUES(1004, 20, '최민수');
INSERT INTO 직원 VALUES(1005, 20, '이용갑');
INSERT INTO 직원 VALUES(1006, 30, '박종일');
INSERT INTO 직원 VALUES(1007, 30, '박미경');
```

① `SELECT DISTINCT COUNT(부서코드) FROM 직원 WHERE 부서코드 = 20;`

② `DELETE FROM 부서 WHERE 부서코드 = 20;`
   `SELECT DISTINCT COUNT(부서코드) FROM 직원;`

답:
- ① 3 (부서코드=20인 직원 3명 → COUNT 결과 3, DISTINCT는 결과 1행에 적용되므로 그대로 3)
- ② 4 (ON DELETE CASCADE로 기획부 직원 3명 함께 삭제 → 7-3 = 4)

---

---

## 2022년 3회 · 문제 12

- 출처: `2022년_3회.md`
- 분류: SQL

학생(STUDENT) 테이블에 전기과 학생이 50명, 전산과 학생이 100명, 전자과 학생이 50명 있다고 할 때, 다음 SQL문 ①, ②, ③의 실행 결과로 표시되는 튜플의 수를 쓰시오. (단, DEPT 필드는 학과를 의미한다)

① `SELECT DEPT FROM STUDENT;`
② `SELECT DISTINCT DEPT FROM STUDENT;`
③ `SELECT COUNT(DISTINCT DEPT) FROM STUDENT WHERE DEPT = '전산과';`

답:
- ① 200 (전체 튜플 수, 중복 제거 없음)
- ② 3 (DISTINCT → 전기과, 전산과, 전자과)
- ③ 1 (COUNT 결과는 항상 1행)

---

---

## 2023년 1회 · 문제 13

- 출처: `2023년_1회.md`
- 분류: SQL

〈학생〉 테이블에서 '이름'이 "민수"인 튜플을 삭제하고자 한다. 다음 〈처리조건〉을 참고하여 SQL문을 작성하시오.

〈처리조건〉
- 최소한의 코드로 작성될 수 있도록 SQL문을 구성한다.
- 명령문 마지막의 세미콜론(;)은 생략이 가능하다.
- 인용 부호가 필요한 경우 작은따옴표(' ')를 사용한다.

답: DELETE FROM 학생 WHERE 이름 = '민수'

---

---

## 2023년 1회 · 문제 16

- 출처: `2023년_1회.md`
- 분류: SQL

다음 〈성적〉 테이블에서 과목별 점수의 평균이 90점 이상인 '과목이름', '최소점수', '최대점수'를 검색하고자 한다. 〈처리조건〉을 참고하여 적합한 SQL문을 작성하시오.

〈성적〉
| 학번 | 과목번호 | 과목이름 | 학점 | 점수 |
|------|----------|----------|------|------|
| a2001 | 101 | 컴퓨터구조 | 6 | 95 |
| a2002 | 101 | 컴퓨터구조 | 6 | 84 |
| a2003 | 302 | 데이터베이스 | 5 | 89 |
| a2004 | 201 | 인공지능 | 5 | 92 |
| a2005 | 302 | 데이터베이스 | 5 | 100 |
| a2006 | 302 | 데이터베이스 | 5 | 88 |
| a2007 | 201 | 인공지능 | 5 | 93 |

〈결과〉
| 과목이름 | 최소점수 | 최대점수 |
|----------|----------|----------|
| 데이터베이스 | 88 | 100 |
| 인공지능 | 92 | 93 |

〈처리조건〉
- 최소한의 코드로 작성될 수 있도록 SQL문을 구성한다.
- WHERE문은 사용하지 않는다.
- GROUP BY와 HAVING을 이용한다.
- 집계함수(Aggregation Function)를 사용하여 명령문을 구성한다.
- '최소점수', '최대점수'는 별칭(Alias)을 위한 AS문을 이용한다.
- 명령문 마지막의 세미콜론(;)은 생략이 가능하다.
- 인용 부호가 필요한 경우 작은따옴표(' ')를 사용한다.

답: SELECT 과목이름, MIN(점수) AS 최소점수, MAX(점수) AS 최대점수 FROM 성적 GROUP BY 과목이름 HAVING AVG(점수) >= 90

---

---

## 2023년 2회 · 문제 4

- 출처: `2023년_2회.md`
- 분류: SQL

다음 〈학생〉 테이블에 (9816021, '한국산', 3, '경영학개론', '050-1234-1234')인 데이터를 삽입하고자 한다. 〈처리조건〉을 참고하여 적합한 SQL문을 작성하시오.

〈학생〉
| 학번 | 이름 | 학년 | 신청과목 | 연락처 |
|------|------|------|----------|--------|
| 9815932 | 김태산 | 3 | 경영정보시스템 | 050-5234-1894 |
| 9914511 | 박명록 | 2 | 경제학개론 | 050-1415-4986 |
| 0014652 | 이익명 | 1 | 국제경영 | 050-6841-6781 |
| 9916425 | 김혜리 | 2 | 재무관리 | 050-4811-1187 |
| 9815945 | 이지영 | 3 | 인적자원관리 | 050-9785-8845 |

〈처리조건〉
- 최소한의 코드로 작성될 수 있도록 SQL문을 구성한다.
- 명령문 마지막의 세미콜론(;)은 생략이 가능하다.
- 인용 부호가 필요한 경우 작은따옴표(' ')를 사용한다.

답: INSERT INTO 학생 VALUES (9816021, '한국산', 3, '경영학개론', '050-1234-1234')
(모든 속성에 값을 넣으므로 속성명 목록 생략 가능)

---

---

## 2023년 2회 · 문제 17

- 출처: `2023년_2회.md`
- 분류: SQL

다음 〈처리조건〉에 부합하는 〈SQL문〉이 완성되도록 괄호에 적합한 옵션을 쓰시오.

〈처리조건〉
- 〈학생〉 뷰를 제거한다.
- 〈학생〉 뷰를 참조하는 모든 데이터도 연쇄적으로 제거한다.

〈SQL문〉
```sql
DROP VIEW 학생 (        );
```

답: CASCADE
(참조 데이터까지 연쇄 삭제 ↔ RESTRICT는 참조 중이면 삭제 취소)

---

---

## 2023년 3회 · 문제 8

- 출처: `2023년_3회.md`
- 분류: SQL

〈R〉과 〈S〉 테이블에 대해 〈SQL문〉을 실행하였을 때 나타나는 결과를 작성하시오. (SQL을 실행하였을 때 출력되는 속성명과 값들을 모두 답안에 적으시오.)

〈R〉
| A | B |
|---|---|
| 1 | a |
| 2 | b |
| 3 | c |

〈S〉
| A | B |
|---|---|
| 1 | a |
| 2 | c |
| 4 | d |

〈SQL문〉
```sql
SELECT A FROM R
UNION
SELECT A FROM S
ORDER BY A DESC;
```

답:

| A |
|---|
| 4 |
| 3 |
| 2 |
| 1 |

(UNION은 중복 제거 → {1,2,3,4}를 내림차순 정렬)

---

---

## 2024년 1회 · 문제 12

- 출처: `2024년_1회.md`
- 분류: SQL

다음 〈R1〉과 〈R2〉 테이블을 참조하여 〈SQL문〉을 실행했을 때 출력되는 결과를 쓰시오. (SQL을 실행하였을 때 출력되는 속성명과 값들을 모두 답안에 적으시오.)

〈R1〉
| A | B | C |
|---|---|---|
| 1 | a | x |
| 2 | b | y |
| 3 | c | t |

〈R2〉
| C | D | E |
|---|---|---|
| x | k | k |
| y | k | t |
| z | p | k |

〈SQL문〉
```sql
SELECT B
FROM R1
WHERE C IN (SELECT C FROM R2 WHERE D='k');
```

답:

| B |
|---|
| a |
| b |

(R2에서 D='k'인 C는 x, y → R1에서 C가 x, y인 행의 B = a, b)

---

---

## 2024년 1회 · 문제 17

- 출처: `2024년_1회.md`
- 분류: SQL

〈EMP_TBL〉 테이블을 참고하여 〈SQL문〉의 실행 결과를 쓰시오.

〈EMP_TBL〉
| EMPNO | SAL |
|-------|------|
| 100 | 1500 |
| 200 | 3000 |
| 300 | 2000 |

〈처리 조건〉
```sql
SELECT COUNT(*) FROM EMP_TBL WHERE EMPNO > 100 AND SAL >= 3000 OR EMPNO = 200;
```

답: 1
(AND가 OR보다 우선 → (EMPNO>100 AND SAL>=3000) OR EMPNO=200 → EMPNO 200 한 행만 해당)

---

---

## 2024년 2회 · 문제 10

- 출처: `2024년_2회.md`
- 분류: SQL

다음에 제시된 〈학생〉과 〈학부〉 테이블에 대한 릴레이션 스키마를 참고하여 각 SQL문의 요구 사항에 맞도록 괄호(①~④)에 알맞은 답을 적어 SQL문을 완성하시오.

릴레이션 스키마
- 〈학생〉 : 학번(PK), 이름, 나이, 학과
- 〈학부〉 : 학번(PK), 이름, 주소, 나이

〈SQL 1〉문
[요구사항] 신입생 정보가 확인되어 〈학부〉 테이블에 신입생 정보를 추가한다.
```sql
INSERT INTO 학부(학번, 이름, 주소, 나이) ( ① ) (240912, '최재균', '서울', 20);
```

〈SQL 2〉문
[요구사항] 〈SQL 1〉문에서 추가한 학생을 〈학부〉 테이블에서 검색한 후 검색된 자료를 〈학생〉 테이블에 추가한다.
```sql
INSERT INTO 학생(학번, 이름, 나이, 학과) ( ② ) 학번, 이름, 나이, '컴퓨터공학' FROM 학부 WHERE 이름 = '최재균';
```

〈SQL 3〉문
[요구사항] 〈학생〉 테이블의 모든 자료를 조회한다.
```sql
SELECT * ( ③ ) 학생;
```

〈SQL 4〉문
[요구사항] 학생이 휴학 신청해서 해당 학생의 '학과' 필드의 값을 "휴학"으로 변경한다.
```sql
UPDATE 학생 ( ④ ) 학과 = '휴학' WHERE 학번 = 240912;
```

답:
- ① VALUES
- ② SELECT
- ③ FROM
- ④ SET

---

---

## 2024년 3회 · 문제 3

- 출처: `2024년_3회.md`
- 분류: SQL

다음 〈employee〉와 〈project〉 테이블을 참조하여 〈SQL문〉을 실행했을 때 출력되는 결과를 쓰시오.

〈employee〉
| no | first_name | last_name | project_id |
|----|------------|-----------|------------|
| 1 | John | Doe | 10 |
| 2 | Jim | Carry | 20 |
| 3 | Rachel | Redmond | 10 |

〈project〉
| project_id | name |
|------------|-------|
| 10 | Alpha |
| 20 | Beta |
| 10 | Gamma |

〈SQL문〉
```sql
SELECT count(*)
FROM employee AS e JOIN project AS p ON e.project_id = p.project_id
WHERE p.name IN (
    SELECT name FROM project p WHERE p.project_id IN (
        SELECT project_id FROM employee GROUP BY project_id HAVING count(*) < 2
    )
);
```

답: 1
(HAVING count(*)<2인 project_id = 20 → name 'Beta' → 조인 결과 5행 중 Beta에 해당하는 행은 Jim 1건)

---

---

## 2025년 1회 · 문제 6

- 출처: `2025년_1회.md`
- 분류: SQL

다음 〈emp〉와 〈sal〉 테이블을 참조하여 〈SQL문〉을 실행했을 때 출력되는 결과를 쓰시오.

〈emp〉
| id | name |
|------|--------|
| 1002 | 홍길동 |
| 1004 | 강감찬 |
| 1006 | 김유신 |
| 1008 | 이순신 |

〈sal〉
| id | incentive |
|------|-----------|
| 1002 | 300 |
| 1004 | 400 |
| 1008 | 1000 |
| 1009 | 500 |

〈SQL문〉
```sql
SELECT name, incentive
FROM emp, sal
WHERE emp.id = sal.id and incentive >= 500;
```

답:

| name | incentive |
|------|-----------|
| 이순신 | 1000 |

(id 일치: 1002, 1004, 1008 중 incentive >= 500은 1008 이순신뿐)

---

---

## 2025년 3회 · 문제 7

- 출처: `2025년_3회.md`
- 분류: SQL

〈A〉 테이블과 〈B〉 테이블을 참고하여 〈SQL문〉의 실행 결과를 쓰시오.

〈A〉
| NAME |
|------|
| Smith |
| Allen |
| Scott |

〈B〉
| RULE |
|------|
| S% |
| %T% |

〈SQL문〉
```sql
SELECT COUNT(*) CNT FROM A CROSS JOIN B WHERE A.NAME LIKE B.RULE;
```

답: 4
(CROSS JOIN 6행 중 LIKE 만족: Smith-'S%', Scott-'S%', Smith-'%T%', Scott-'%T%' → 4)

---

---

## 2025년 3회 · 문제 20

- 출처: `2025년_3회.md`
- 분류: SQL

다음 〈A〉 테이블을 참조하여 〈SQL문〉을 실행했을 때 출력되는 결과를 쓰시오. (〈A〉 테이블에 표시된 'NULL'은 값이 없음을 의미한다.)

〈A〉
| COL1 | COL2 |
|------|------|
| 2 | NULL |
| 3 | 6 |
| 2 | 3 |
| NULL | 3 |
| 4 | 5 |

〈SQL문〉
```sql
SELECT COUNT(COL2)
FROM A
WHERE COL1 IN (2, 3)
    OR COL2 IN (3, 5);
```

답: 4
(WHERE 조건에 5행 모두 해당하지만 COUNT(COL2)는 NULL 제외 → 4)

---

---

## 2026년 1회 · 문제 9

- 출처: `2026년_1회.md`
- 분류: SQL

아래 조건을 참고하여 각 SQL 구문을 실행했을 때 반환되는 행(Row)의 수를 쓰시오. (단, DEPT 칼럼은 학과명이다.)

〈테이블 조건〉
STUDENT 테이블에는 다음 세 학과의 학생 정보가 저장되어 있다.
컴퓨터과 50명 · 인터넷과 100명 · 사무자동화과 50명

〈SQL 구문〉
1. `SELECT DEPT FROM STUDENT;`
2. `SELECT DISTINCT DEPT FROM STUDENT;`
3. `SELECT COUNT(DISTINCT DEPT) FROM STUDENT WHERE DEPT = '컴퓨터과';`

답:
- 1. 200
- 2. 3
- 3. 1

---

---

## 2026년 1회 · 문제 10

- 출처: `2026년_1회.md`
- 분류: SQL

아래는 선수(PLAYER) 정보를 관리하는 테이블을 정의하는 SQL 문이다. 팀(TEAM) 테이블의 특정 칼럼을 참조하는 외래키 제약 조건을 추가하려 할 때, 괄호 ①~⑤에 들어갈 적절한 예약어(keyword) 또는 칼럼명을 아래 조건을 참고하여 쓰시오.

〈조건〉
- 외래키 제약 조건의 이름은 TEAM_TF로 지정한다.
- PLAYER 테이블의 TEAM_ID 칼럼이 외래키 역할을 한다.
- TEAM 테이블의 TEAM_ID2 칼럼을 참조 대상으로 한다.

```sql
CREATE TABLE PLAYER (
  PLAYER_ID   CHAR(7)      NOT NULL,
  PLAYER_NAME VARCHAR2(20) NOT NULL,
  TEAM_ID     CHAR(3)      NOT NULL,
  PRIMARY KEY (PLAYER_ID),
  ( ① ) TEAM_TF
  ( ② ) KEY ( ③ )
  ( ④ ) TEAM ( ⑤ )
);
```

답:
- ① CONSTRAINT
- ② FOREIGN
- ③ TEAM_ID
- ④ REFERENCES
- ⑤ TEAM_ID2
(CONSTRAINT 제약명 FOREIGN KEY (열) REFERENCES 테이블(열))

---

---

## 2026년 1회 · 문제 18

- 출처: `2026년_1회.md`
- 분류: SQL

다음은 SQL에 대한 문제이다. 아래 코드를 확인하여 알맞은 출력값을 작성하시오.

```sql
SELECT COUNT(*)
FROM employee e
JOIN dept d ON e.dep_id = d.dept_id
WHERE d.budget > (
    SELECT AVG(budget) FROM dept
);
```

답: 2
(부서 예산 평균보다 예산이 큰 부서에 속한 직원 수. ※ 복원본에 employee/dept 테이블 데이터가 누락되어 있음 — 정답은 복원 답안 기준)

---

---

## 2020년 2회 · 문제 6

- 출처: 복원 문제(chobopark.tistory.com)
- 분류: SQL

학생 테이블(학번, 이름, 학년, 수강과목, 점수, 연락처)에서 아래 조건을 만족하는 SQL문을 작성하시오.

1) 3, 4학년인 학번, 이름을 조회한다.
2) IN 연산자를 사용해야 한다.

답: SELECT 학번, 이름 FROM 학생 WHERE 학년 IN (3, 4);

---

---

## 2020년 2회 · 문제 12

- 출처: 복원 문제(chobopark.tistory.com)
- 분류: SQL

학생 테이블의 NAME 속성에 IDX_NAME이라는 이름으로 인덱스를 생성하는 SQL문을 작성하시오.

답: CREATE INDEX IDX_NAME ON 학생(NAME);

---

---

## 2020년 3회 · 문제 20

- 출처: 복원 문제(chobopark.tistory.com)
- 분류: SQL

학생 테이블에 주소 속성을 추가하는 SQL문의 괄호를 채우시오.

( ① ) TABLE 학생 ( ② ) 주소 VARCHAR(20);

답:
- ① ALTER
- ② ADD
(속성 삭제는 DROP COLUMN, 변경은 ALTER/MODIFY)

---

---

## 2020년 4회 · 문제 16

- 출처: 복원 문제(chobopark.tistory.com)
- 분류: SQL

다음 조건을 만족하면서 학과별로 튜플 수가 얼마인지 구하는 SQL문을 작성하시오.

- WHERE 구문을 사용하지 않는다. / GROUP BY를 사용한다. / 별칭(AS)을 사용해야 한다. / 집계 함수를 사용해야 한다.
- 〈학생〉 테이블: 학과(전기 1명, 컴퓨터 2명, 전자 2명), 결과 속성: 학과, 학과별튜플수

답: SELECT 학과, COUNT(학과) AS '학과별튜플수' FROM 학생 GROUP BY 학과;
(처리조건에 "별칭은 작은따옴표 사용"이 명시된 회차라 따옴표 포함 표기)

---

---

## 2021년 2회 · 문제 6

- 출처: 복원 문제(chobopark.tistory.com)
- 분류: SQL

다음 SQL에서 JOIN할 경우 괄호 안에 알맞은 답을 쓰시오.

SELECT ... FROM 학생정보 a JOIN 학과정보 b ( ① ) a.학과 = b.( ② )

답:
- ① ON
- ② 학과

---

---

## 2021년 2회 · 문제 10

- 출처: 복원 문제(chobopark.tistory.com)
- 분류: SQL

'이름' 컬럼에서 '이'로 시작하는 문자열을 내림차순 정렬하는 쿼리의 괄호를 채우시오.

SELECT ... FROM ... WHERE 이름 LIKE ( ① ) ORDER BY 컬럼명 ( ② )

답:
- ① '이%'
- ② DESC

---

---

## 2021년 3회 · 문제 3

- 출처: 복원 문제(chobopark.tistory.com)
- 분류: SQL

GRANT의 기능에 대해 간략하게 약술하시오.

답: 사용자(User)에게 접속 권한, 오브젝트 생성 권한, DBA 권한 등을 부여하는 명령어
(↔ REVOKE: 부여한 권한을 회수하는 명령어. 둘 다 DCL)

---

---

## 2022년 1회 · 문제 4

- 출처: 복원 문제(chobopark.tistory.com)
- 분류: SQL

점수(score)를 기준으로 내림차순 정렬하여 조회하는 SQL문의 괄호를 채우시오.

SELECT name, score FROM 성적 ( ① ) BY ( ② ) ( ③ )

답:
- ① ORDER
- ② score
- ③ DESC
(※ 복원본의 결과 그림은 소실되었으나 정렬 쿼리 구문 문제)

---

---

## 2022년 2회 · 문제 3

- 출처: 복원 문제(chobopark.tistory.com)
- 분류: SQL

H회사의 전체 제품 단가보다 큰 제품을 출력하고자 한다. 괄호 안에 들어갈 알맞은 용어를 쓰시오.

SELECT 제조사, 제품명, 단가
FROM 제품
WHERE 단가 > ( ) (SELECT 단가 FROM 제품 WHERE 제조사 = 'H')

답: ALL
(ALL: 서브쿼리의 모든 값보다 커야 함 / ANY(SOME): 하나라도 크면 됨)

---

---
