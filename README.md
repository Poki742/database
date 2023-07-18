# database

## oracle sql developer를 이용하여 사용자 추가하기

classmanager 라는 유저를 생성하고 비밀번호는 classmanager로 만들고<br>
기본 테이블스페이스는 users 임시 테이블스페이스는 temp 로 만든다.<br>

``` sql
CREATE TABLE admin_table
(
    idx NUMBER(4) not NULL,
    admin_id VARCHAR2(20) not NULL,
    admin_pw VARCHAR2(20) not NULL
);
```
