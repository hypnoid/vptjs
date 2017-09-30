# 2.4 getNum

如果所给数字是已定义的将返回原值，否则返回所给的返回值，默认返回'-'。

###  参数
+ param : 字符串
+ reStr : 自定义返回值

### 引用
+ [isDefine]()

###  代码
``` js
getNum(param,reStr) {
   let re = this.isDefine(param) ? param : '-';
   if(reStr){
      re=this.isDefine(param) ? param : reStr
   }
   return re;
}
```