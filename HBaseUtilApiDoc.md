**1.创建HTable实例**

`public static HTable HbaseTableGetByName(String tableName)`

调用示例：
```
//传入参数为表的名称。这里需要复制hbase-site.xml,hdfs-site.xml,core-site.xml文件到项目的resources目录下，系统会自动识别来读取配置选项
//或者可以使用Configuration类来配置Zookeeper的地址等配置项，这里使用第一种方式
HTable table = HbaseTableGetByName(tableName);
```

**2.全表扫描**

`public static void scanData(HTable table)`

调用示例：
```
HTable table = HbaseTableGetByName(tableName);
scanData(table);
```

**3.按照rowkey进行查询**

`public static Map<String,String> get(HTable table,String rowKey)`

调用示例：
```
String rowKey = "key";
get(table,rowkey);
//这里不知道具体业务，只选择打印了值为中文的列，后期可按照需求修改代码
```

**4.插入数据**

`public static void putData(HTable table,String cf,String rowKey,Map<String,String> keyValue)`

```
//指定列簇
String cf="cf";
//指定rowKey
String rowKey = "key";
Map<String,String> keyValue = new HashMap<String,String>();
//添加需要加入的列值对
keyValue.put("column1","value1");
keyValue.put("column2","value2");
putData(table,cf,rowKey,keyValue);
```

**5.删除数据**

`public static void deleteData(HTable table,String rowKey,String cf,List<String> columns)`

```
List<String> columns = new ArrayList<String>();
//添加需要删除的列名
columns.add("column1");
columns.add("column2");
deleteData(table,rowKey,cf,columns);
```
