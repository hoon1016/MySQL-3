# MySQL-3

### 1.MySQL에서 between 과 not between 사용법

- between이란 숫자들 사이의 값을 between으로 나타 낼수 있다.예시로 

-  select * from books

-  where released_year between 2004 and 2015;

- 이런식으로 쓸수 있으며 식으론 select * from books where 컬럼명 between 숫자 and 숫자; 이런식으로 쓸수 있고

- not between는 앞에 그냥 not을 쓰면 해당 숫자의 사이가 포함되지않는것을 화면에 출력 할 수 있다.
 
 ### 2. MySQL에서 in 과 not in 사용법
 - MySQL에서는 리스트가 없다.여러개의 값들이 포함 된 값을 가지고 올때 in을 사용해서 해당하는 데이터를 가져올 수 있다.

- 예시로 select * from books where released_year in (2017,1985,2010,2014,2008); 이렇게 쓸수 있으며 식으로 표현하면

- select * from books where 컬럼명 in (값,값,값,값,값);

- 이런식으로 쓸 수 있고 not in 을 쓰면 그 값이 해당하지않는 데이터들만 화면에 출력된다.
 
### 3. MySQL에서 Case End 조건식 사용법

- 파이썬에 if조건문과 같은 맥락이라고 보면된다 예시로 

- select title,released_year,
-   case 
-		when released_year >= 2000 then 'Modern'
-       else '20th Century'
-	  end as genre
- from books;

- 이런식으로 쓸수 있고 식으로 나타 내면 

-select 컬럼명,컬럼명,
-	  case 
-		  when 컬럼명 >= 값 then '원하는 문장'
-        else '원하는 문장'
-	  end as 원하는 컬럼명
- from books;

- 이렇게 식으로 나타낼수 있으며 case 쓰기전에 꼭 ,를 찍어야지 오류가 안난다.

### 4. MySQL에서 join문 만드는 방법
- join 문을 쓸려면 일단 테이블 2개 이상이 필요 하고 2개를 합칠때 쓰는 함수이다.
-예시를 아래에 적어놨다.
- select s.title, r.rating
- from Series s
- join Reviews r
-	 on s.id = r.series_id
- order by s.title;

- 이런식으로 쓸 수 있고 식으로 나타내면 

- select 테이블 컬럼명, 테이블 컬럼명
- from Tables 1 
- join Tables 2
-	 on Table1.id = Tanles2_id
- order by 테이블 컬럼명;

- 이런식으로 쓸수 있다 테이블이 총 3개 이상이라면 아래를 참고 하면 된다.

- select 테이블 컬럼명, 테이블 컬럼명
- from Tables 1 
- join Tables 2
-	 on Table1.id = Tanles2.id
- join Tables 3
-  on Table1.id = Tanles3.id
- order by 테이블 컬럼명;

- 이런식으로 쓸수 있다.

### 5. 여러 테이블 설계 시,foreign key 사용법

- foreign key이란 Tables 여러개 만들때 id를 연결하기 위해 쓰는 함수이다.

- create table Tables1(
-	 id int auto_increment primary key,
-  컬럼1,
-  컬럼2,
-  컬럼3
- );
- create table Tables2(
-	 id int auto_increment primary key,
-  컬럼1,
-  컬럼2
- );

- create table Tables3(
-	 id int auto_increment primary key,
-  컬럼1,
-  Tables1_id,
-  Tables2_id,
-  foreign key(Tables1_id)references Tables1(id),
-  foreign key(Tables2_id)references Tables2(id)
- );

- 위에 예시처럼 Tables3에서 기존 Tables1,Tables2 id를 연결하여 쓸 수 있게 해주는게 foreign key이다.
- 또한 테이블 만들때 컬럼명은 여러개 만들어도 상관없다 

### 6. MySQL 의 ifnull()함수,if()함수 사용법

- ifnull()함수는 데이터 안에 비어있는 데이터가 있으면 그 데이터 안에 비어있는 데이터 이름을 바꿀수 있게 해주는 함수이다.
- select s.first_name,ifnull(avg(p.grade),0) as average
- from students s
- left join papers p
-	 on s.id = p.student_id
- group by s.first_name 
- order by p.grade desc;

- 위에 있는 예시로 참고 하면되고 식으로 나타내면

- select 컬럼명,ifnull(컬럼명,0)
- from Tables1
- join Tables2
-	 on Tables1.id = Tables2.id;
- 이런식으로 쓸 수 있다.

- if() 함수는 case와 같은 맥락인 느낌이다.

