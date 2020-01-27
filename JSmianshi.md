### 1、prototype是什么，怎么理解原型链
prototype称之为对象的原型,但是null对象没有。它和另外一个对象相关联。每一个对象都从原型继承属性，就需要用到prototype。比如｛｝这个对象，他继承的属性是Object.prototype. 那么Object对象就是原型，它的属性prototype就与｛｝相关联,｛｝继承Object属性。

原型链 举个例子
比如 我创建一个 Array对象 array，这个对象array继承Array类中的prototype，即Array.prototype（也是原型），然后Array中prototype这个属性有继承Object中的prototype.

### 总结
从构造函数和原型对象的角度来讲。构造函数中有一个属性是prototype,指向原型对象，共有的属性会写在原型对象中。实例有一个属性__proto__指向其原型对象，原型对象本身也有属性__proto__指向其原型，这样就形成了原型链

### 2、箭头函数的特点（个人叙述）
首先第一点就是箭头函数没有this,所以说在箭头函数里面如果使用了this对象，那么它就是最近一层的非箭头函数this.

所以一般调用的时候都是默认调用外层的this,同时他没有arguments对象。
不能通过new生成，所以箭头函数没有构造器。个人理解为没有类一样,（类可以new，有构造函数之类的）的功能（暂时这样理解）。

没有原型，所以没有prototype属性。没有super

因为不能使用 new 调用，所以也没有 new.target 值。
根据网上的解释：箭头函数： non-mehtod 就是指不被用作对象属性中的函数

### 3、如何理解arguments对象（个人理解）
因为js不能像c c++ java这样有函数重载的功能，为了能够实现函数重载的功能，js引入arguments对象
每个函数function都会有一个arguments对象，已经实例好了

引用网上arguments的观点
1.arguments对象和Function是分不开的。
2.因为arguments这个对象不能显式创建。
3.arguments对象只有函数开始时才可用。

注意一个点  arguments虽然可以像数组一样使用，但它并不是数组。

详细的属性就不说了，总体来说关键字 重载 映射

### 4、javascript里面 this中 call与apply的区别
这两个方法的目的都是一样的，都是为了改变this的指向。通俗一点的说法就是一个对象调用另一个对象的方法。
这两个的不同点首先体现在参数上面，一个以参数形式进行传递，一个以数组形式进行传递。当参数比较少的时候,两者方法是差不多的。
apply中有arguments对象的传参，参数数量不定
call方法需要手动传入制定参数

##### 举个例子
```
function fengtimo(name,age){
    this.name=name;
    this.age=age;
}
function dazhuti(name,age){
    fengtimo.apply(this,arguments);
    //或者 fengtimo.call(this,name,age)
}
var me =new dazhuti("dalao",18);
console.log(me)  //输出dalao 18 
```

### 5、解释一下ES6中的迭代器
在ES6中，在数组对象里面的原型__proto__里面增加了Symbol的iterator方法。
原型对象中增加了这个方法
###### Symbol(Symbol.iterator): ƒ values()
里面有包含了一个函数，叫next()函数;

第一次调用next函数,指针指向下标0，第二次调用时，下标指向1。当数组遍历完之后，如再调用，输出的值就是undenfined

#####这个是内置对象中增加的方法，实际上我们像平时数组遍历即可。