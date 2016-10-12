Get elastichsearch info

	curl -XGET 'http://localhost:9200'

Get all mappings

	curl -XGET 'http://localhost:9200/{index_name}/_mappings'

Get aliases for all indices (pretty)

	curl -XGET 'http://localhost:9200/_aliases?pretty=1'

Get mappings for a particular field

	curl -XGET 'http://localhost:9200/{index_name}/_mapping/field/{field_name}'

Create an index

	curl -XPUT 'http://localhost:9200/{index_name}'

Reindex

	curl -XPUT 'http://localhost:9200/_reindex -d @{filename.json}'

Example Reindexing JSON:

	{
		"source": {
			"index": "source-index-name"
		},
		"dest": {
			"index": "destination-index-name"
		}
	}

Get Cluster Health:

	curl -XGET http://localhost:9200/_cluster/health?pretty
	
Another endpoint that can be used to access any(most) useful info:

	curl -X GET http://localhost:9200/_cat

To get health:

	curl -X GET http://localhost:9200/_cat/health?v
	
To get list of all shards:

        curl -X GET http://localhost:9200/_cat/shards?v

To get unassigned only shards:
	
	curl -X GET http://localhost:9200/_cat/shards?v | grep UNASSIGNED

To get details and reason for the unassigned shards:
	
	curl -X GET http://localhost:9200/_cat/shards?index,unassigned.reason

To fix unassigned shards with transient settings:

	curl -XPUT http://localhost:9200/_settings -d '{ "number_of_replicas" :0 }'
	
	curl -XPUT http://localhost:9200/_cluster/settings -d '
	{
	    "transient" : {
		"cluster.routing.allocation.enable": true
	    }
	}'

Explore Elasticsearch client API for python
