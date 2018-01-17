
##### Redhat7 安裝前設定

[1]: 檔案open-file max > 65535
````
ulimit -n 
# 65535

# 設定limits
sudo vi /etc/security/limits.d/20-nproc.conf

root soft nofile 1000000
root hard nofile 1000000
* soft nofile 1000000
* hard nofile 1000000

````

[2]: max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]

````
sudo vi /etc/sysctl.d/99-sysctl.conf
vm.max_map_count = 300000
````

### Create index initialization

````
curl -XPUT "http://loaclhost:9200/[索引]/"
````

### customize index

* `shards` : 資料分割後即為shards, 一個shards最大存儲文檔數量= Integer.MAX_VALUE-128（2,147,483,519）
* `replicas` : 碎片備份shards數量 * replicas數量 = 總備份數量
````
curl -XPUT "http://loaclhost:9200/[索引]/" -d '{
   "settings": {
       "number_of_shards" :   5,
       "number_of_replicas" : 1
   }
}'
````

### insert data
* `?pretty` : 回傳結果可以閱讀

##### 資料庫關係對應圖:
* `Database` → `Tables` → `Rows` → `Columns`
* `Indices` → `Types` → `Documents` → `Fields`

````
# curl -XPUT "http://loaclhost:9200/[索引]/[屬性]/[編號]"
curl -XPUT "http://loaclhost:9200/[index]/[type]/[id]?pretty" -d '{
[資料]
}'

# 自動產生id則
curl -XPOST curl -XPUT "http://loaclhost:9200/[index]/[type]/?pretty" -d '{

}'

````
### delete index
````
curl -XDELETE http://localhost:9200/[index]/[type]
````
* `create` → 只允許建立document
* `index` → 允許建立document,如果已存在就取代舊document
* `update` → 更新document
* `delete` → 刪除指定document

### multi insert data 
````
curl -XPOST "localhost:9200/ping/demo/_bulk?pretty=1" -d '
{"index":{}}
{//JSON//}
'
````
