---
title: vue生命周期
date: 2018-10-24 14:33:57
tags: VUE
---
>VUE生命周期

<font color="#F8A131">生命周期分为八个部分：创建前beforeCreate，创建后created，挂载前beforeMount，挂载后mounted，更新前beforeUpdate，更新后updated，销毁前beforeDestory，销毁后destroyed</font>

1. beforeCreate---实例创建前：这个阶段实例的data、methods是读不到的
2. created---实例创建后：这个阶段已经完成了数据观测(data observer)，属性和方法的运算， watch/event 事件回调。mount挂载阶段还没开始，$el 属性目前不可见，数据并没有在DOM元素上进行渲染
3. beforeMount---在挂载开始之前被调用：相关的 render 函数首次被调用
4. mounted---el选项的DOM节点 被新创建的 vm.$el 替换，并挂载到实例上去之后调用此生命周期函数。此时实例的数据在DOM节点上进行渲染
5. beforeUpdate---数据更新时调用，但不进行DOM重新渲染，在数据更新时DOM没渲染前可以在这个生命函数里进行状态处理
6. updated---这个状态下数据更新并且DOM重新渲染，当这个生命周期函数被调用时，组件 DOM 已经更新，所以你现在可以执行依赖于 DOM 的操作。当实例每次进行数据更新时updated都会执行
7. beforeDestory---实例销毁之前调用
8. destroyed---Vue 实例销毁后调用。调用后，Vue 实例指示的所有东西都会解绑定，所有的事件监听器会被移除，所有的子实例也会被销毁。


<font color="#F8A131">vue生命周期在真实场景下的业务应用:</font>

1. created：进行ajax请求异步数据的获取、初始化数据
2. mounted：挂载元素内dom节点的获取
3. nextTick：针对单一事件更新数据后立即操作dom
4. updated：任何数据的更新，如果要做统一的业务逻辑处理
5. watch：监听具体数据变化，并做相应的处理

<font color="#F8A131">如何解释vue的生命周期才可以令面试官满意?</font>

<font color="#456782">知识点①：</font>
1. breforeCreate()：实例创建前，这个阶段实例的data和methods是读不到的。
2. created()：实例创建后，这个阶段已经完成数据观测，属性和方法的运算，watch/event事件回调,mount挂载阶段还没有开始。$el属性目前不可见，数据并没有在DOM元素上进行渲染。
3. 在谈及Vue的生命周期时，我们首先需要创建一个实例，也就是在new Vue（）的对象过程中，首先执行了init（init是vue组件里面默认去执行的），在init的过程中首先调用beforeCreate，然后在injections（注射）和reactivity（反应性）的时候，再去调用created，所以在init的时候，事件已经调用了，我们在beforcreate的时候千万不要去修改data里面的赋值的数据，最早也要放在created里面去做（添加一些行为）

<font color="#456782">知识点②：</font>
1. beforeMount：在挂载开始之前被调用：相关的 render 函数首次被调用。
2. mounted：el选项的DOM节点 被新创建的 vm.$el 替换，并挂载到实例上去之后调用此生命周期函数。此时实例的数据在DOM节点上进行渲染
3. 在create完成之后，它会去判断instance（实例）里面是否含有“el”option（选项），如果没有的话。他会调用vm.$mount(el)这个方法，然后执行下一步；如果有的话，直接执行下一步。紧接着会判断时候含有“template”这个选项 ，如果有的话，他会把template解析成render function，这是一个template编译的过程，结果是解析成了render函数。
```
render (h) {
  return h('div', {}, this.text)
}
```
  (render函数：传参h就是Vue里面的createElement方法，return返回一个createElement方法，其中要传三个参数，第一个参数就是要创建的div标签，第二个参数穿了一个对象，对象里面可以是我们组件上面的props，或者是事件之类的东西；第三个参数就是div标签里面的内容，这里指向了data里面的text）

    使用render函数的结果和我们之前使用template解析出来的结果是一样的。render函数是发生在breforeMount和mount之间的，这也从侧面说明了，在breforeMount的时候，$el还只是我们在HTML里面写的节点，然后到Mount的时候，他就把渲染出来的内容挂载到了Dom节点上，这种的中间的过程其实是执行了render function的内内容。

  beforeMount在有了render function的时候才会执行，当执行完render  function之后就会调用mounted这个钩子，在mounted挂载完毕之后，这个实例就算是走完了流程。

  后续的钩子函数执行的过程都是需要外部 的触发才会执行。比如，有数据的变化，会调用beforeUpdate，然后经过Virtual  Dom，最后updated更新完毕，当组件被销毁的时候，会调用beforeDestory，以及destoryed。

  钩子函数其实和回调函数是一个概念，当系统执行到某处时，检查是否有hook，有则回调。（每一个组件都有属性，方法和事件。所有的生命周期都归于事件，在某个时刻自动执行）。
