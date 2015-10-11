## ElasticSearch  9200

1. 다운&설치
```
 wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.5.2.tar.gz
```

2. 기본적인 plugin설치 http://develop.sunshiny.co.kr/1010
```
$> bin/plugin --list
$> bin/plugin --remove head
$> bin/plugin --install mobz/elasticsearch-head   //http://localhost:9200/_plugin/head/
$> bin/plugin --install lukas-vlcek/bigdesk     //http://localhost:9200/_plugin/bigdesk/
$> bin/plugin --install lmenezes/elasticsearch-kopf  // http://localhost:9200/_plugin/kopf/
$> bin/plugin -i elasticsearch/marvel/latest // http://any-server-in-cluster:9200/_plugin/marvel
```

3. 실행 & 중지
```
$> bin/elasticsearch -d (d는 백그라운드로)

$> curl -XPOST localhost:9200/_shutdown
```
 curl 'http://localhost:9200/?pretty' 를 입력해서 결과가 제대로 오는지 체크
설

---

### contents
- ElasticSearch System
   - 데이터 indexing
   - ElasticSearch 데이터구조 : Index / Type / Document
   - ElasticSearch 시스템구조 : Cluster / node

- Data Handling
   - basic 데이터처리
   - QueryDSL : Query / Filter

---

- 데이터구조
   - Database -> Index
   - Table -> Type
   - Row -> Document : 데이터가 저장되는 최소의 단위

   - column -> Field
   - schema -> mapping

- REST API : POST / GET / PUT / DELETE
   ```
   $ curl -X{methon} http://{hostIP}:{port}/{Index}/{Type}/{Document id} -d '{...data...}'

   $ curl localhost:9200  // health check

   - pretty=true  //결과를 JSON형시으로 포매팅해서 보여줌
   - _source 필드 : JSON형시으로 데이터가 저장된다.
   - _version 필드 : test
   ```
---
### 검색
- Searching
- Aggregation
- QueryDSL
- Filter

---
### 스키마
- Mapping : 데이터의 저장형태와 검색엔진에서 해당 데이터에 어떻게 접근하고 처리하는지에 대한 명세. 즉 스키마

---
### 분석
- Analysis
