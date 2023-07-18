# database

## oracle sql developer를 이용하여 사용자 추가하기

유저를 생성하고 비밀번호를 만들고(각각 classmanager)<br>
기본 테이블스페이스는 users 임시 테이블스페이스는 temp 로 만든다.<br>

```sql
create user classmanager
IDENTIFIED by classmanager
DEFAULT TABLESPACE users
TEMPORARY TABLESPACE temp;
```

권한 부여<br>

``` sql
GRANT CONNECT to classmanager;
GRANT RESOURCE to classmanager;
GRANT dba to classmanager; 
```

## 성적DB 데이터베이스 접속 후 테이블 생성
![image](https://github.com/Poki742/database/assets/126844692/34d852ac-486e-4648-bf61-c4d86a787716)<br>

테이블 생성<br>

``` sql
CREATE TABLE admin_table
(
    idx NUMBER(4) not NULL,
    admin_id VARCHAR2(20) not NULL,
    admin_pw VARCHAR2(20) not NULL
);
```
테이블에 있는 idx에 기본 키를 주는 'admin_idx_pk' 이름의 제약조건을 추가한다.<br>
``` sql
ALTER TABLE admin_table add
(
    CONSTRAINT admin_idx_pk PRIMARY KEY(idx)
);
```
1부터 시작하여 값이 자동으로 증가하는 'admin_idx_pk' 시퀀스를 만듦
``` sql
CREATE SEQUENCE grade_idx_pk START with 1;
```
'admin_table'에 idx, admin_id, admin_pw 열에 해당하는 값을 삽입하는 작업을 함.
``` sql
INSERT INTO grade_table (idx, num, name, sub1, score1, sub2, score2, sub3, score3, total, avg)
VALUES(grade_idx_pk.nextval, 21108, '심상윤', '문학', 26, '한국사', 32, '실용영어', 67, 125, 42);
```
