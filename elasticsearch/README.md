# ElasticSearch


ElasticSearch version: 1.3.1

Plugins installed:

* Marvel
* mapper-attachement
* BigDesk
* Inquisitor


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


echo '>>> Building new image'
# Due to a bug in Docker we need to analyse the log to find out if build passed (see https://github.com/dotcloud/docker/issues/1875)
sudo docker build ./deploy | tee /tmp/docker_build_result.log
RESULT=$(cat /tmp/docker_build_result.log | tail -n 1)
if [[ "$RESULT" != *Successfully* ]];
then
  exit -1
fi