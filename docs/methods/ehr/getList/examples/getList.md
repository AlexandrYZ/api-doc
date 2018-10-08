[Работа с ЭМЗ](../../index.md)
==============================

### ![GET](../../../../img/get.png) [/ehr/getList`?patient_id={patient_id}`](../index.md)

### Примеры

**Request:** GET `http://tempurl.com/ehr/getList?patient_id=65:33650 HTTP/1.1`

**Response**

```json
{
    "result":[
        {
            "id":"#879:35649",
            "patient_id":"#65:33650",
            "summary":"",
            "dz":{
                "mkb_code":"C40.1",
                "mkb_name":"Коротких костей верхней конечности",
                "tnm":{
                    "t":{
                        "code":"NONE",
                        "caption":""
                    },
                    "n":{
                        "code":"NONE",
                        "caption":""
                    },
                    "m":{
                        "code":"NONE",
                        "caption":""
                    },
                    "g":{
                        "code":"NONE",
                        "caption":""
                    }
                },
                "dz_stage":{
                    "code":"NONE",
                    "caption":""
                }
            }
        },
        {
            "id":"#880:35540",
            "patient_id":"#65:33650",
            "summary":"",
            "dz":{
                "mkb_code":"C50.2",
                "mkb_name":"Верхневнутреннего квадранта молочной железы",
                "tnm":{
                    "t":{
                        "code":"NONE",
                        "caption":""
                    },
                    "n":{
                        "id":"2",
                        "code":"N_0",
                        "caption":"0"
                    },
                    "m":{
                        "code":"NONE",
                        "caption":""
                    },
                    "g":{
                        "code":"NONE",
                        "caption":""
                    }
                },
                "dz_stage":{
                    "code":"NONE",
                    "caption":""
                }
            }
        }
    ]
}
```