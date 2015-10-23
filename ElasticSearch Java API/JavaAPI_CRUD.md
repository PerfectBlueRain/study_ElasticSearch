### CRUD(GET, DELETE, UPDATE, Bulk)

#### Get API
- GetResponse / prepareGet()
```
GetResponse response = client.prepareGet("twitter", "tweet", "1")
                             .execute()
                             .actionGet();
```

#### Delete API
- DeleteResponse / prepareDelete()
```
DeleteResponse response = client.prepareDelete("twitter", "tweet", "1")
                             .execute()
                             .actionGet();
```

#### Update API
- UpdateRequest / prepareUpdate()
```
//1. UpdateRequest
UpdateRequest updateRequest = new UpdateRequest();
updateRequest.index("index");
updateRequest.type("type");
updateRequest.id("1");
updateRequest.doc(jsonBuilder()
        .startObject()
            .field("gender", "male")
        .endObject());
client.update(updateRequest).get();

//2. prepareUpdate()
client.prepareUpdate("ttl", "doc", "1")
        .setDoc(...json...)
        .get();

//3.
UpdateRequest updateRequest = new UpdateRequest("ttl", "doc", "1")
                                    .script("ctx._source.gender = \"male\"");
client.update(updateRequest).get();
```

#### Bulk API
- BulkRequestBuilder / prepareBulk()
- BulkProcessor : offers a simple interface to flush bulk operations automatically based on the number or size of requests, or after a given period

```
```
