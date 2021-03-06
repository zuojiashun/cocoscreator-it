> ##guide-demo 

- [x] cus-on-emit(自定义事件)

> ###事件机制说明：<br >
> 一句话,事件机制可以解决这种需求：`某个条件达成才做某事` <br >

> ###监听 <br >

```javascript
   node.on('eventName',callback,target);
```

> 参数一：`eventName` 事件名 用于区别监听的事件类型<br >
> 参数二: `callback` 回调函数 当事件名所描述的条件发生时，触发该函数<br >
> 参数三：`target` 调用者， 指定调用该回调函数的调用者,通常是回调函数所处的这个对象(this),也可以动态指定别的对象来调用回调函数。<br >

> ###发射 <br >

```javascript
   node.emit('eventName',detail);
```

> 参数一：`eventName` 事件名 用于区别监听的事件类型<br >
> 参数二: `detail` 传递给回调函数的参数<br >

> ###回调<br >
```javascript
   callback(event);
```
> 参数一：`event` 事件 emit发送的信息在`event.detail`<br >

> ###一对一流程<br >
> `A发消息给B`<br >
> 实际上并不存在A发消息给B这种功能，而是`B监听A`， `A朝天喊`，`监听的人自然能听到并作出反应` <br >
> 一句话, `一支穿云箭，千军万马来相会~` <br >
> 首先B要监听A <br >

```javascript
   this.A.on('hello!',this.doAction,this); //this is B 
```

> 然后A朝天喊 <br >

```javascript
   this.node.emit('hello!','my name is A'); //this is A
```

> 最终B就会听到 <br >

```javascript
   doAction:function(event){
        let msg = event.detail;  // 'my name is A'
   }
```

> 其他的一对多， 多对多，都由上面的模式发展而来




