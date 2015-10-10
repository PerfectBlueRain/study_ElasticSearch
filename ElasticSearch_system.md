# ElasticSearch System구조
- config/elasticsearch.yml : 시스템구조 설정파일
```
cluster.name : "bookSystem"

node.name : "Box"
node.master : true
node.data : false

index.number_of_shards : 3
index.number_of_replicas : 1
```

## Cluster & Node
- cluster는 시스템단위 / node는 프로세스단위
- 서로다른 클러스터는 데이터 접근, 교환을 할수없다.
- 노드는 각 하나의 엘라스틱 프로세스를 실행한다. 노드단위로프로세스를 실행
   ```
   $bin/elasticsearch --node.name=Box
   ```
- master / data node

## Shard & Replica
- shard는 루씬에서 사용되는 메커니즘으로 데이터 검색을 위해 구분되는 최소의 단위 인스턴스. index된 데이터는 여러개의 shard로 분리되어 저장됨
- Replica는 Failover데이터손실을 방지 / 최초샤드와 복사본을 동시에 검색해서 성능향상
- 사용되는 index단위로 데이터를 처리하고, 엘라스틱서치가 직접노드를 분산시키는 작업을하는것
   ```
   $ curl -XPUT localhost:9200/books -d'
   {
      "settings" : {
         "number_of_shards" : 3,
         "number_of_replicas" : 1
      }
   }
   '
   ```
