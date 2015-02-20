# snaptap
Simple daemon to replicate data between cassandradb and elasticsearch

## Usage

    snaptap [-f] [-d] -i <interval> -m <mapping>
    -f    Run in foreground mode
    -d    Run in debug mode
    -i    Interval in seconds for syncing the databases
    -m    Path to the mapping file

## Mapping

You must create a file containing the mapping between the tables in CassandraDB and ElasticSearch, in the JSON format.  For example:

    {
        "mapping": [
            ["keyspace.users", "index.users"]
        ]
    }

In the example above, the script will keep in sync the table "users" on keyspace "keyspace" in the CassandraDB with the table "users" on the index "index" in ElasticSearch.

## Before you go

The index in ElasticSearch must have the timestamp enabled, so the script will be able to know which version of the data is the most current.  Refer to the [ElasticSearch documentation](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/indices-create-index.html) to learn more bout how to create the index.
