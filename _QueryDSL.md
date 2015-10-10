## Query
- 검색에 사용되는 질의 문법을 QueryDSL
- query는 *관련성(relevance)*를 계산하여, 결과문서에 *_score*를 부여한다. 이 점수기준으로 매칭된 문서를 정렬하게된다
- Query는 일반적으로 전문검색에사용, scoring점수계산하고, 결과값을 캐싱하지않음, 응답속도도 느리다.

![queryDSL](http://drive.google.com/uc?export=view&id=0B0CgSzgDruziVU1sY09OU0loZ2M)
- 파라미터
   - timeout / from / size / search_type / query_cache / terminate_after
