# 2.5 getPartStr

截取字符串


### # 参数

+ str : 字符串 
+ begin : 索引开始位置
+ end : 索引结束位置
+ [suffix] : 后缀

### # 代码
``` js
setDate(str, begin, end, suffix) {
let newStr= this.setStr(str);
newStr = (newStr !== '-' ? newStr.substring(index1, index2) - 0 : '-') + suffix;
if(suffix){
    newStr += suffix;
}
return newStr;
}
```

### 引用


### # 用法
    setDate('201708',4, 6, '月')
    => '8月'

    setDate('20170930',4, 6, '月')
    => '9月'

    setDate('20170930',6, 8, '日')
    => '30日'
