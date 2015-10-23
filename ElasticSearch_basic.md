# ElasticSearch basic

- 데이터구조
Database -> Index
Table -> Type
Row -> Document : 데이터가 저장되는 최소의 단위

```
//REST API
$ curl -X{methon} http://{hostIP}:{port}/{Index}/{Type}/{Document id} -d '{...data...}'

$ curl localhost:9200  // health check
```
---
- pretty=true :결과를 JSON형시으로 포매팅해서 보여줌
- _source 필드 : JSON형시으로 데이터가 저장된다.
- _version 필드 : test

---

# CRUD

- 데이터확인
   ```
   - GET
   $ curl -XGET localhost:9200/books/book/1?pretty=true
   $ curl -XGET localhost:9200/books/book/1/_source?pretty=true
   ```

- 데이터입력
   ```
   - POST : 데이터입력 (임의의 Document id를 생성해준다)
   $ curl -XPOST localhost:9200/books/book/1 -d'
      {
         "title" : "ElasticSearch Guide",
         "author" : "Kim",
         "started" : "2014-03-14",
         "pages" : 250
      }'

   - PUT : 데이터수정 /입력
   $ curl -XPUT localhost:9200/books/book/1 -d'
      {
         "title" : "ElasticSearch Guide",
         "author" : ["Kim", "Lee"],
         "started" : "2014-03-14",
         "pages" : 250
      }'
   ```

- 데이터삭제
   ```
   - DELETE : 데이터삭제 ( Type단위삭제 / Document단위삭제)
   $ curl -XDELETE localhost:9200/books/book/1
   $ curl -XDELETE localhost:9200/books/book
   ```

- 업데이트API
   - _update

- 벌크API : 배치작업
   - _bulk

```
curl -XPOST localhost:9200/
