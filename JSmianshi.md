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