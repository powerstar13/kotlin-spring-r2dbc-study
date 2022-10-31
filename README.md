# 스프링 데이터 R2DBC

1. 전통적인 방식의 `JDBC(Java Database Connectivity)` 드라이버는 하나의 커넥션에 하나의 스레드를 사용하는 `Thread per Connection` 방식
    - Thead per Connection 방식은 데이터베이스로부터 응답을 받기 전까지 스레드는 블로킹됨
    - 높은 처리량과 대규모 애플리케이션을 위해 비동기-논블로킹 데이터베이스 API에 대한 요구가 생김
    - 애플리케이션 로직이 비동기-논블로킹이더라도 DB 드라이버가 JDBC라면 필연적으로 블로킹이 발생하므로 100% 비동기-논블로킹의 성능을 내기 어려웠음
    - 오라클의 `ADBA(Asynchronous Database Access API)` 프로젝트가 표준화 진행 중 지원 종료됨
2. `R2DBC(Reactive Relational Database Connectivity)`는 빠르게 성장 중인 리액티브 기반의 비동기-논블로킹 데이터베이스 드라이버
    1. Oracle, Postgres, H2, MSSQL, Google Spanner, MariaDB, 리액티브 스트림 구현체인 Project Reactor, RxJava 등을 지원한다.
3. `스프링 데이터 R2DBC`는 R2DBC 기반의 스프링 데이터 프로젝트다.
    1. **스프링 WebFlux와 스프링 데이터 R2DBC를 같이 사용하면 전 구간 비동기-논블로킹 애플리케이션을 구현할 수 있다.**
    2. 많은 ORM(JPA)에서 제공하는 LazyLoading, Dirty-Checking, Cache 등을 지원하지 않으므로 ORM으로써의 기능은 적지만, 오히려 더 심플하게 사용할 수 있다.
    3. `ReactiveCrudRepository`는 리액티브를 지원하는 CRUD 인터페이스다.
    4. 스프링 데이터 JPA와는 다르게 데이터클래스와 val 프로퍼티를 사용할 수 있다.
4. 이 외에도 스프링 데이터 MongoDB Reactive, 스프링 데이터 Redis Reactive도 있다.
