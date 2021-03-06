# 编辑知识图谱

## 接口
- `createEntity(headId, relationId, tailId, name, comment, nameEn, nameCn, division, from)`

  新增头实体或尾实体，新建头实体则headId为空，新建尾实体则tailId为空，relationId不可为空，后面的参数是新建的实体的属性（若无则置空）  
  成功则返回新建实体的id  

- `createProperty(name, comment, nameEn, nameCn, division, from, domain, range)`

  新增关系实体  
  成功则不会返回有效内容  

- `createLink(headId,relationId,tailId)`

  向三个已知实体添加关联（在图中新增一条线）  
  成功则不会返回有效内容  

- `updateItem(id, name, comment, nameEn, nameCn, division, from, domain, range)`

  item可以是一个entity，也可以是一个property  
  全图同步更新  
  成功则不会返回有效内容  

- `replaceItem(String id, String headId, String relationId, String tailId, String name, String comment, String nameEn, String nameCn, String division, String from, String domain, String range);`

  `headId relationId tailId`是要修改的三元组

  `id`是修改的节点

  其余是修改后的属性

- `deleteItem(id)`

  删除该item的信息，同时删除所有与它关联的三元组，但不会删除其他item的信息  
  成功则不会返回有效内容  

- `deleteLink(headId,relationId,tailId)`

  删除某个三元组，但其中的三个item的信息都会被保留  
  成功则不会返回有效内容  
  方法的参数类型均为String 

## 说明

entity(head/tail) property(relation) triple(link)的示例如下(jsonStr形式)

@entity 
```json
{  
    "id": "#公共卫生间保持通风。每日随时进行卫生清洁，保持地面、墙壁清洁，洗手池无污垢，便池无粪便污物积累。每日对便池进行消毒。",  
    "comment": "",  
    "recordId": "138930",  
    "nameEn": "",  
    "nameCn": "",  
    "division": "String",  
    "from": "http://www.openkg.cn/COVID-19/prevention"  
}  
```

@property
```json
{
    "id": "P023",
    "comment": "",
    "recordId": "95189", 
    "nameEn": "Use of transportation", 
    "nameCn": "使用交通工具", 
    "from": "http://www.openkg.cn/COVID-19/prevention", 
    "domain": "C3", 
    "range": "C6"
}
```

@triple
```json
{
    "head": "95699", 
    "relation": "125296", 
    "tail": "95495"
}
```
