### ElasticSearch Java API
- https://www.elastic.co/guide/en/elasticsearch/client/java-api/current/client.html
- gradle추가 & Refresh All
```
compile 'org.elasticsearch:elasticsearch:1.5.2'
```

### Client / Index / CRUD(GET, DELETE, UPDATE) / SEARCH / Aggregation
#### Client
	- Node Client

	```
	// on startup
	Node node = nodeBuilder().node();

	//cluster.name: yourclustername
	Node node = nodeBuilder().clusterName("yourclustername").node();

	// Embedded node clients behave just like standalone nodes
	Node node = nodeBuilder()
        .settings(ImmutableSettings.settingsBuilder().put("http.enabled", false))
        .client(true)
    	.node();

    //  "local" here means local on the JVM (well, actually class loader) level, meaning that two local servers started within the same JVM will discover themselves and form a cluster.
    Node node = nodeBuilder().local(true).node();

	Client client = node.client();

	// on shutdown
	node.close();
	```

   - Transport Client

   ```
   // connects remotely to an Elasticsearch cluster using the transport module
   Client client = new TransportClient()
        .addTransportAddress(new InetSocketTransportAddress("host1", 9300))
        .addTransportAddress(new InetSocketTransportAddress("host2", 9300));

   //
   Settings settings = ImmutableSettings.settingsBuilder()
        .put("cluster.name", "myClusterName").build();
   Client client = new TransportClient(settings);

   //
   Settings settings = ImmutableSettings.settingsBuilder()
        .put("client.transport.sniff", true).build();
   TransportClient client = new TransportClient(settings);
   ```
      -  transport client level setting
         - client.transport.sniff
         - client.transport.ignore_cluster_name
         - client.transport.ping_timeout
         - client.transport.nodes_sampler_interval

#### Index API
   - generate JSON
   - Index Document
   ```
   // send IndexResponse
   IndexResponse response = client.prepareIndex("twitter", "tweet")
        .setSource(json)
        .execute()
        .actionGet();

   // get IndexResponse
   String _index = response.getIndex(); // Index name
   String _type = response.getType(); // Type name
   String _id = response.getId();  // Document ID (generated or not)
   long _version = response.getVersion(); // Version
   boolean created = response.isCreated(); // isCreated() is true if the document is a new one
   ```
