### JSON generate
   - 1.usually (aka do it yourself) using native byte[] or as a String
   ```
   String json = "{" +
     "\"user\":\"kimchy\"," +
     "\"postDate\":\"2013-01-30\"," +
     "\"message\":\"trying out Elasticsearch\"" +
   "}";
   ```

   - 2.Map
   ```
   Map<String, Object> json = new HashMap<String, Object>();
   json.put("user","kimchy");
   json.put("postDate",new Date());
   json.put("message","trying out Elasticsearch");
   ```

   - 3.serialize beans such as Jackson
   ```
   // instance a json mapper
   ObjectMapper mapper = new ObjectMapper(); // create once, reuse

   // generate json
   byte[] json = mapper.writeValueAsBytes(yourbeaninstance);
   ```

   - 4.Using built-in ElasticSearch helpers XContentFactory.jsonBuilder()
   ```
   XContentBuilder builder = jsonBuilder()
   .startObject()
     .field("user", "kimchy")
     .field("postDate", new Date())
     .field("message", "trying out Elasticsearch")
   .endObject()

   String json = builder.string();
   ```
