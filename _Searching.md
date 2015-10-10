## Searching
- 질의는 Type, Index그리고 여러개의 index를 묶어서 멀티 인덱스범위로 질의가능
- Multi Tenancy
```
$>  GET .../{index}/{Type}/_search

$> curl -XGET localhost:9200/books,magazines/_search?q=time
$> curl -XGET localhost:9200/_all/_search?q=time  //모든인덱스검색
```

### URL방식( String Search)
- q
- df
- default_operator
- explain
- source
- fields
- sort
- from
- timeout
- size
- search_type

### Request Body방식( QueryDSL Search)
```
{host}:{port}/{Index}/{Type}/_search -d '{
   <옵션> : <값>, ...
   "query" : {
      ...<질의 문법>...
   }
}'
```
- 옵션
   - from, size, fields,
   - sort
   - _source : include / exclude
   - partial_fields, fielddata_fields
   - highlight : field, pre_tags / post_tags
   ```
   GET _search
   {
       "from":0,
       "size":50,
       "sort":{"_score":{"order":"desc"}},
       "fields":["@version"],
       "explain":true
   }
   ```

- 검색
   - "term"
   - Filtered Search "filtered"
   - Full-text Search "match"
   - Phrase Search "match_phrase"
   ```
   GET _search
   {
       "from":0,
       "size":50,
       "query": {
           "match" : {
               "host" : "new-ats-edge01"
           }
       }
   }
   ```
