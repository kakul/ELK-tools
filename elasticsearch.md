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

Explore Elasticsearch client API for python