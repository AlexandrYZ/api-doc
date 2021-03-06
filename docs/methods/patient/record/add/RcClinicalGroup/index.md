## Добавление статистической записи 'Установка клинической группы' (RcClinicalGroup) указанному пациенту 

### ![POST](../../../../../img/post.png) /patient/record/add
* **Request:** [RcClinicalGroup](../../../../../types/types.md#com.siams.med.api.Rc.RcClinicalGroup) **record** <patient_id, RcClinicalGroup>
* **Response:** [[RcClinicalGroup](../../../../../types/types.md#com.siams.med.api.Rc.RcClinicalGroup)]

Статистическая запись 'Установка клинической группы' добавляется как запись [Rc](../../../../../types/types.md#com.siams.med.api.Rc) указанному пациенту.

### Пример http

**Request**

POST `http://dev.onco-reg.ru/api/1.0/json/patient/record/add HTTP/1.1`

```json
{
    "record":{
        "patient_id":"#71:33568",
        "rc_clinical_group":{
            "group_type":{
                "code":"NONE"
            }
        }
    }
}
```

**Response**
```json
{
    "result":[
        {
            "id":"#1081:13388",
            "class_name":"RcClinicalGroup",
            "patient_id":"#71:33568",
            "ehr_id":"#1055:33568",
            "published":{
                "user_id":"#961:170",
                "time":"2018-10-08 23:49:03"
            },
            "org_unit_id":"#999:28",
            "time_rc":"2018-10-08 23:49:03",
            "rc_clinical_group":{
                "group_type":{
                    "code":"NONE",
                    "caption":""
                }
            }
        }
    ]
}
```



### Пример java 

```java
public class AddRcClinicalGroup {
    public static void main(String[] args) throws IOException {
        final ProtoBuffClient client = newProtoBuffClient();

        Patients.Patient patient = getPatient();

        Records.Rc rc = client.addPatientRecord(Records.Rc.newBuilder()
                .setPatientId(patient.getId())
                .setRcClinicalGroup(Records.Rc.RcClinicalGroup.newBuilder()
                        .setGroupType(Directories.ClinicalGroupType.newBuilder().setCode("NONE"))
                )
                .build());

        Records.Rc.RcClinicalGroup rcClinicalGroup = rc.getRcClinicalGroup();
        Directories.ClinicalGroupType groupType = rcClinicalGroup.getGroupType();
    }
}

```
