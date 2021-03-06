## Добавление статистической записи 'Хирургическое лечение' в указанное заболевание (RcOper)

### ![POST](../../../../../img/post.png) /ehr/record/add
* **Request:** [Rc](../../../../../types/types.md#com.siams.med.api.Rc) **record** <patient_id> <ehr_id> <[rc_oper](../../../../../types/types.md#com.siams.med.api.Rc.RcOper)>
* **Response:** [[Rc](../../../../../types/types.md#com.siams.med.api.Rc). [rc_oper](../../../../../types/types.md#com.siams.med.api.Rc.RcOper)]

Статистическая запись 'Хирургическое лечение' добавляется как запись [Rc](../../../../../types/types.md#com.siams.med.api.Rc) в указанное заболевание.

### Пример http

 **Request**
 
 POST `http://dev.onco-reg.ru/api/1.0/json/ehr/record/add HTTP/1.1`
 ```json
 {
     "record":{
         "patient_id":"#65:33650",
         "ehr_id":"#879:35649",
         "rc_oper":{
             "operation":{
                 "id":"845"
             },
             "condition":{
                 "id":"1"
             },
             "org_unit_id":"#993:1",
             "intra_compl":{
                 "orid":"#665:4",
                 "id":"37",
                 "caption":"01.36. Травма паренхимы печени"
             },
             "after_compl":{
                 "orid":"#665:4",
                 "id":"37",
                 "caption":"01.36. Травма паренхимы печени"
             },
             "srv":[
                 {
                     "code":"SRV_1_1_5",
                     "caption":"Регионарных лимфатических узлов без первичной опухоли",
                     "group":1,
                     "index":5
                 }
             ]
         }
     }
 }
 ```
 
 **Response `200`**
 
 ```json
 {
     "result":[
         {
             "id":"#1265:14654",
             "class_name":"RcOper",
             "patient_id":"#65:33650",
             "ehr_id":"#879:35649",
             "published":{
                 "user_id":"#961:160",
                 "time":"2018-10-04 23:58:34"
             },
             "org_unit_id":"#999:28",
             "time_rc":"2018-10-04 23:58:34",
             "rc_oper":{
                 "operation":{
                     "orid":"#678:115",
                     "id":"845",
                     "caption":"Д06. ДРУГИЕ МЕТОДЫ"
                 },
                 "condition":{
                     "id":"1",
                     "code":"AMB",
                     "caption":"амбулаторно"
                 },
                 "org_unit_id":"#993:1",
                 "intra_compl":{
                     "orid":"#665:4",
                     "id":"37",
                     "caption":"01.36. Травма паренхимы печени"
                 },
                 "after_compl":{
                     "orid":"#665:4",
                     "id":"37",
                     "caption":"01.36. Травма паренхимы печени"
                 },
                 "srv":[
                     {
                         "code":"SRV_1_1_5",
                         "caption":"Регионарных лимфатических узлов без первичной опухоли",
                         "group":1,
                         "index":5
                     }
                 ]
             }
         }
     ]
 }
 ```
 
### Пример java

```java
public class AddRcOper {
    public static void main(String[] args) throws IOException {
        final SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        final Patients.Patient patient = getPatient();
        final Patients.EHR ehr = getEhr();
        final ProtoBuffClient client = newProtoBuffClient();
        final Directories.DrNK0439 compl = getDr();
        final Directories.Srv59Oper srv = getSrv();
        final Directories.MedOrg medOrg = getMedOrg();

        Records.Rc newEhrRecord = client.addEhrRecord(Records.Rc.newBuilder()
                .setPatientId(patient.getId())
                .setEhrId(ehr.getId())
                .setRcOper(Records.Rc.RcOper
                        .newBuilder()
                        .setOperation(Directories.DrNK0465.newBuilder().setId("845").build())
                        .setCondition(Directories.TherapyCond.newBuilder().setId("1").build())
                        .setOrgUnitId(medOrg.getOrgUnitId())
                        .setIntraCompl(compl)
                        .setAfterCompl(compl)
                        .addSrv(srv)
                        .build())
                .build());

        String id = newEhrRecord.getId();
        Records.Rc.RcOper rcOper = newEhrRecord.getRcOper();
    }
}
```
