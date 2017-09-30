# 2.3 getStr

如果所给字符串是已定义的将返回原值，否则返回所给的返回值，默认返回'-'。

###  参数
+ param : 字符串
+ reStr : 自定义返回值

###  代码
``` js
getStr(param,reStr){
    let re = this.isDefine(param) ? param : '-';
    if(reStr){
        re=this.isDefine(param) ? param : reStr
    }
    return re;
}
```

### 引用
+ [isDefine]()

### 用法

        let param1;
        setStr(param1);
        => '-'

        let param2=null;
        setStr(param2);
        => '-'

        let param3='this is string.';
        setStr(param3);
        => 'this is string.'