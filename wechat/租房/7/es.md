# 列出所有索引

```json
列出所有索引（列出所有的数据库）

GET /_cat/indices?v
```

# 添加索引

```json
PUT /goods
{
  "settings": {
      // 副本数
    "number_of_replicas": 1,
      // 分片数
    "number_of_shards": 5
  }
}
```

# 删除索引

```json
DELETE /goods
```

# 修改文档

```json
POST /goods/_doc/1/_update
{
 "doc": {"price":100 }
}
```

# 查询(搜索)

```json
GET /goods/_search

// 查询是xiaomi9的
GET /goods/_search
{
  "query": {
    "match": {
      "title": "xiaomi9"
    }
  }
}

// 排序
GET /goods/_search
{
  "query": {
    "match_all": {}
  },
  "sort": [
    {
      "_id": {
        "order": "desc"
      }
    }
  ]
}


## 进行中文分词搜索

PUT /goods
{
  "mappings": {
    "_doc":{
      "properties":{
        "name":{
          "type":"text",
          "analyzer":"ik_max_word",
          "search_analyzer":"ik_max_word"
        },
        "desn":{
          "type":"text",
          "analyzer":"ik_max_word",
          "search_analyzer":"ik_max_word"
        }
      }
    }
  }
}
```



# PHP操作ES

官网：<https://www.elastic.co/guide/en/elasticsearch/client/php-api/current/index.html> 

## 创建索引

```php
$hosts = [
    '127.0.0.1:9200'
];
$client = \Elasticsearch\ClientBuilder::create()->setHosts($hosts)->build();

// 创建索引
$params = [
    'index' => 'goods',
    'body' => [
        'settings' => [
            'number_of_shards' => 5,
            'number_of_replicas' => 1
        ],
        'mappings' => [
            '_doc' => [
                '_source' => [
                    'enabled' => true
                ],
                'properties' => [
                    'title' => [
                        'type' => 'keyword'
                    ],
                    'desn' => [
                        'type' => 'text',
                        'analyzer' => 'ik_max_word',
                        'search_analyzer' => 'ik_max_word'
                    ]
                ]
            ]
        ]
    ]
];
$response = $client->indices()->create($params);
```

## 更新文档

```php
$hosts = [
    '127.0.0.1:9200',
];
$client = \Elasticsearch\ClientBuilder::create()->setHosts($hosts)->build();
// 写文档
$params = [
    'index' => 'goods',
    'type' => '_doc',
    'id' => $model->id,
    'body' => [
        'title' => $model->title,
        'desn' => $model->desn,
    ],
];
$response = $client->index($params);
```

## 搜索

```php
$hosts = [
    '127.0.0.1:9200',
];
$client = \Elasticsearch\ClientBuilder::create()->setHosts($hosts)->build();
$params = [
    'index' => 'goods',
    'type' => '_doc',
    'body' => [
        'query' => [
            'match' => [
                'title'=>[
                    'query' => '手机'
                ]
            ]
        ]
    ]
];
$results = $client->search($params);
dump($results);
```



