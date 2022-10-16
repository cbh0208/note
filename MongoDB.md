



### 常用命令



#### db

- `db`  查询当前数据库名

- `db.version()`  查询数据库版本

- `db.stats()`  显示当前数据库状态

- `show dbs` 展示所有数据库

- `db.getMongo()`  查看当前数据库链接机器地址

- `use  [db]  `创建/切换数据库

  ```
  > use music
  switched to db music
  ```

- `db.dropDatabase()`  删除当前数据库

- `exit`退出



#### Collection

- `db.createCollection(name, options)`  创建集合

  ```
  > db.createCollection('a')
  { "ok" : 1 }
  ```

- `show collections`  查看已有集合

- `db.getCollectionNames()`   查看已有集合(以数组形式返回)

- `db.[collection].renameCollection("[name]")`  重命名集合

  ```
  > db.c.renameCollection("clsn")
  { "ok" : 1 }
  ```

- `db.[collection].drop()` 删除集合

  ```
  > db.love.drop()
  true
  ```

  



#### document

##### 增

- `db.[collection].insert([document or array of documents])` 将文档插入到集合中(可多可单)(少用)

  ```
  > db.love.insert({"name":"鸢一折纸","id":"angel","blood":"A"})
  WriteResult({ "nInserted" : 1 })
  
  > db.love.insert([{"name":"五河琴里","id":"efreet"},{"name":"夜刀神香","id":"priness"}])
  BulkWriteResult({
          "writeErrors" : [ ],
          "writeConcernErrors" : [ ],
          "nInserted" : 2,
          "nUpserted" : 0,
          "nMatched" : 0,
          "nModified" : 0,
          "nRemoved" : 0,
          "upserted" : [ ]
  })
  ```

- `db.[collection].insertOne()`  将单个文档插入到集合中

  ```
  > db.love.insertOne({"name":"鸢一折纸","id":"angel"})
  {
          "acknowledged" : true,
          "insertedId" : ObjectId("60f16294b61897958a83a607")
  }
  ```

- `db.[collection].insertMany()`  将多个文档插入到集合中

  ```
  > db.love.insertMany([{"name":"五河琴里","id":"effert"},{"name":"夜刀神十香","id":"princess"}])
  {
          "acknowledged" : true,
          "insertedIds" : [
                  ObjectId("60f1636bb61897958a83a608"),
                  ObjectId("60f1636bb61897958a83a609")
          ]
  }
  ```

- `db.[collection].save()  `如果 _id 主键存在则更新数据，如果不存在就插入数据





##### 删

- `db.[collection].remove()`   删除

  ```
  > db.love.remove({"id":"Nightware"})
  WriteResult({ "nRemoved" : 1 })
  ```

  

##### 改

- `db.[collection].update()`   更新       （不存在时是否创建,是否全部插入）

  ```
  > db.love.update({"name":"时崎狂三"},{$set:{"id":"Nightware"}})
  WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
  
  > db.love.update({"name":"时崎狂三"},{$set:{"height":"157"}},true,true)
  WriteResult({ "nMatched" : 2, "nUpserted" : 0, "nModified" : 2 })
  ```

  



##### 查

- `db.[collection].find()`  

  ```
  > db.love.find()
  { "_id" : ObjectId("60f14bb20daa777de3f2ca45"), "name" : "鸢一折纸", "id" : "angel", "blood" : "A" }
  
  > db.love.find({"name":"五河琴里"})
  { "_id" : ObjectId("60f1636bb61897958a83a608"), "name" : "五河琴里", "id" : "effert" }
  ```

  | 操作       | 格式                     | 范例                                        | RDBMS中的类似语句       |
  | :--------- | :----------------------- | :------------------------------------------ | :---------------------- |
  | 等于       | `{<key>:<value>`}        | `db.col.find({"by":"菜鸟教程"}).pretty()`   | `where by = '菜鸟教程'` |
  | 小于       | `{<key>:{$lt:<value>}}`  | `db.col.find({"likes":{$lt:50}}).pretty()`  | `where likes < 50`      |
  | 小于或等于 | `{<key>:{$lte:<value>}}` | `db.col.find({"likes":{$lte:50}}).pretty()` | `where likes <= 50`     |
  | 大于       | `{<key>:{$gt:<value>}}`  | `db.col.find({"likes":{$gt:50}}).pretty()`  | `where likes > 50`      |
  | 大于或等于 | `{<key>:{$gte:<value>}}` | `db.col.find({"likes":{$gte:50}}).pretty()` | `where likes >= 50`     |
  | 不等于     | `{<key>:{$ne:<value>}}`  | `db.col.find({"likes":{$ne:50}}).pretty()`  | `where likes != 50`     |



#### 











