## Aggregation
- 데이터를 단순히 저장하고 불러오는 기능뿐아니라 데이터 값의 카운트, 합계등을 계산하는 다양한처리기능
- near-real time analytic 도구
- 리포팅, 대시보드 생성에 적합
---
- buckets
   - criteria을 만족하는 Document집합
   - 주어진 조건에 해당하는 Document를 버킷이라는 저장소 단위로 구분해서 담아 새로운 데이터 집합을 형성한다.
   - 버킷별로 또다시 하위 어그리게이션을 통해 버킷이 있는 데이터로 다시 새로운 어그리게이션 연산을 반복해서 수행
   - filter / missing / terms / range / histogram
- metrics
   - 우리가 알고싶은 정보, bucket에 표함된 Document에대한 statistics
   - min / max / sum / avg

```
{
   "aggs" : {
      "<이름>" : {
         "<타입>" : {
            ...<문법>...
         }
      [, "aggs": {..하위 어그리게이션}]
      }
   [, "<이름2>" : {...}]
   }
}
```
### Aggregation종류
- basic Aggregation
   - min / max / avg / sum / value_count
- approximation
   - cardinality
   - percentile
- significant-terms
