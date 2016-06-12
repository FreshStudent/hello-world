###### 1.遍历MyMap中的List  
- 遍历map  可以直接取出map中的key 和value
```
    String hisStdCode = "";
    for(MyMap map : recordList){
        hisStdCode = map.getString("hisStdCode");
        for(MyMap newMap: newList){
            if(hisStdCode.equals(newMap.getString("hisStdCode"))){
                for (Map.Entry<String, Object> entry : newMap.entrySet()) {  
                    if (!isNotUpdateCloum(noUpdateMap,entry.getKey())) {
                        map.put(entry.getKey(), entry.getValue()) ;
                    }
                } 
                newRecordList.add(map);
                break;//找到第一个相匹配的，更新信息后就可以跳出内循环。
            }
        }
    }
```

###### 2.List根据近特定字段升序排序（是的，我就是用来测试的 好吗？不好意思 你这逗逼，哈哈哈哈哈  说的就是你）
```
    //2016-1-18  AddBy  exportExcelList需要根据HisStandardCode升序排序
    Collections.sort(exportExcelList,new Comparator<MyMap>(){
        public int compare(MyMap map1,MyMap map2){
            String str1 = map1.get("HISSTANDARDCODE").toString();   
            String str2 = map2.get("HISSTANDARDCODE").toString();   
            return str1.compareTo(str2);
        }
    });
```

