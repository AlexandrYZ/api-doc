[Работа с вложениями](../index.md)
==================================

### ![POST](../../../../img/post.png) [/attachment/query](../index.md)

**Request**

POST `http://tempurl.com/attachment/query HTTP/1.1`
```json
{
    "query":{
        "ids":[
            "#1585:422"
        ]
    }
}
```

**Response**
```json
{
    "result":[
        {
            "id":"#1585:422",
            "digest":"6e4a3290ff2ab22fed4e747c95678bbf534b41d0",
            "name":"проверка.txt",
            "type":"text/plain",
            "size":27,
            "created":"2018-10-02 18:53:06"
        }
    ]
}
```

**[Примеры кода](queryAttachment.md)**