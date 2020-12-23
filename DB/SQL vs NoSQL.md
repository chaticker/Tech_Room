### SQL

- 데이터는 정해진(엄격한) 데이터 스키마 (= structure)를 따라 데이터베이스 테이블에 저장됨
- 데이터는 관계를 통해서 연결된 여러개의 테이블에 분산됨
- 종류
  * MySQL
  * PostgreSQL
  * SQLite

### NOSQL(Not Only SQL)

- 스키마, 관계 필요없음
- 조인이 필요없으며, 모든 데이터가 하나의 컬렉션 안에 존재
- 종류
  * Document DB
    - mongoDB: 데이터를 json document 형태로 저장
    - 보통의 SQL처럼 행과 열이 존재하는 것이 아닌 어떤 종류, 어떤 모양이든 원하는 데이터를 모두 저장 가능 
    ![KakaoTalk_20201223_154735185](https://user-images.githubusercontent.com/23302973/102970675-4e102500-453b-11eb-8ebd-58205d1c2c3e.jpg)
  
  * Key Value DB
    - CassandraDB: column wide database 유형 / 읽고 쓰기가 빠름
    - DynamoDB: 서버리스. 분산된 key valueDB로서 아마존이 만들었음 / 매초 24,000개의 읽기 지원
    - 빠르게 많이 쓰거나 읽어야할 때 필요함
  
  * Graph DB
    - column이나 document가 필요없지만 각 노드 사이의 관계를 알아야할 때 사용
    - 예를들어 페이스북을 만든다면 이게 필요함(실제:Tao)
    - 각각의 엔티티를 저장하고 이를 관계망으로 연결함
    ![KakaoTalk_20201223_161732799](https://user-images.githubusercontent.com/23302973/102970678-4f415200-453b-11eb-9f03-7d003b843b6a.jpg)

뭘 써야 좋을까? : 데이터가 그렇게 많지 않다면 SQL로 커버 가능. 데이터가 많고 특별한 이슈에 대응해야 한다면 NOSQL(수평적 확장)
