

wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-5.4.1.tar.gz

bin/elasticsearch-plugin install https://github.com/couchbaselabs/elasticsearch-transport-couchbase/releases/download/2.5.4.1/elasticsearch-transport-couchbase-2.5.4.1.zip

bin/elasticsearch-plugin install x-pack

wget https://artifacts.elastic.co/downloads/kibana/kibana-5.4.1-linux-x86_64.tar.gz







--user elastic:changeme 
curl -XPOST "192.168.188.187:9200/video/demo/" -d '{"account_number":1,"balance":39225,"firstname":"Amber","lastname":"Duke","age":32,"gender":"M","address":"880 Holmes Lane","employer":"Pyrami","email":"amberduke@pyrami.com","city":"Brogan","state":"IL","post_date": "2017-08-07T16:06:22"}





