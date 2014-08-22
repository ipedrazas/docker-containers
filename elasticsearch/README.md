# ElasticSearch

Build the image

    docker build -t ipedrazas/elasticsearch .

Run the image

    docker run -d -p 9200:9200 -p 9300:9300 ipedrazas/elasticsearch

Mounting a volume:

    docker run -d -p 9200:9200 -p 9300:9300 -v /data/elasticsearch:/data ipedrazas/elasticsearch \
        /elasticsearch/bin/elasticsearch -Des.config=/data/es.yml


Create an Index

    curl -XPUT 'http://localhost:9200/twitter/'


Test install

    curl -XGET 'http://localhost:9200'
