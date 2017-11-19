#### 浅拷贝与深拷贝的区别与实现
>浅拷贝：只复制引用对象的指针，而不复制引用对象本身，彼此之间的操作会互相影响。

>深拷贝：复制引用对象本身，在堆中重新分配内存，复制后的对象和引用对象互不影响。

    Note:
    浅拷贝与深拷贝只针对复杂数据类型(Object, Array)，基本数据类型（null, undefined, string, number, boolean）的值本身就存储在堆内存。
    浅拷贝只复制一层对象的属性，深拷贝则递归复制了所有层级。
    浅拷贝就像你和你的影子，你完蛋，你的影子也完蛋；深拷贝就像你和你的克隆人，你完蛋，你的克隆人还活着。

浅拷贝示例
```javascript
  方法一： slice()
  方法二： concat()
  方法三：
  function shallowCopy(src) {
    var dst = {};
    for (var prop in src) {
      if (src.hasOwnProperty(prop)) {
        dst[prop] = src[prop];
      }
    }
    return dst;
  }
```
深拷贝示例
```javascript
  方法一：
  var target = JSON.parse(JSON.stringify(source));
　方法二：
  function deepCopy(p, c) {
    c = c || {};
    for (var i in p){
      if(p.hasOwnProperty(i)){
        if(typeof p[i] === 'Object'){
          c[i] = Array.isArray(p[i]) ? [] : {}
          deepCopy(p[i], c[i]);
        } else {
          c[i] = p[i]
        }
      }
    }
    return c;
  }
```
