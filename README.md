# how-to-install-elasticsearch-ubuntu
how to install elasticsearch ubuntu

## STEP 1: Installing and Configuring Elasticsearch

```
curl -fsSL https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```

```
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
```

```
sudo apt update
```

```
sudo apt install elasticsearch
```

log Elasticsearch
```
cd /var/log/elasticsearch/
```

## Step 2 — Configuring Elasticsearch
```
vi /etc/elasticsearch/elasticsearch.yml
```

```
network.host: localhost
http.host: 0.0.0.0
```

```
sudo systemctl start elasticsearch
```

enable Elasticsearch to start up every time your server boots
```
sudo systemctl enable elasticsearch
```

## Step 3: Enable port ufw
```
sudo ufw allow 9200
```
```
sudo ufw status
```

## Step 4: Open browser and go to URL
```
http://my_ip:9200
```

## Step 5: test elasticsearch
```
curl -X GET -H "Content-Type: application/json" 'http://localhost:9200'
```

1/ get all nodes
```
curl -XGET -H "Content-Type: application/json" 'http://localhost:9200/_nodes?pretty'
```

2/ create new records
```
curl -XPOST -H "Content-Type: application/json" 'http://localhost:9200/tutorial/helloworld/1?pretty' -d '{"test":["aaa","bbb","cccc"]}'
```

+ tutorial is the index of the data in Elasticsearch.
+ helloworld is the type.
+ 1 is the ID of our entry under the above index and type.


3/ get a records
```
curl -X GET -H "Content-Type: application/json" 'http://localhost:9200/tutorial/helloworld/1?pretty'
```

4/ put a records
```
curl -XPUT -H "Content-Type: application/json" 'http://localhost:9200/tutorial/helloworld/1?pretty' -d '{"test":["aaa2","bbb100","cccc"]}'
```


## Additional links
Document APIs
```
https://www.elastic.co/guide/en/elasticsearch/reference/current/docs.html#docs
```

Elasticsearch documentation
```
https://www.elastic.co/guide/en/elasticsearch/reference/7.6/index.html
```
