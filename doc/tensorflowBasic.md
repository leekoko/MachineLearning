# Tensorflow的基础使用   

### 1.变量&常量

Z：变量和常量的使用Demo如下

```python
import tensorflow as tf
data1 = tf.constant(2.5)
data2 = tf.Variable(10,name = 'var')
# 输出变量，常量相关信息
print(data1)
print(data2)
# session输出常量的值
sess = tf.Session()
print(sess.run(data1))
# session输出变量的值
init = tf.global_variables_initializer()  # 变量需要先初始化
sess.run(init)
print(sess.run(data2))
sess.close()
```

输出结果：

```
Tensor("Const_8:0", shape=(), dtype=float32)
<tf.Variable 'var_7:0' shape=() dtype=int32_ref>
2.5
10
```

Z：如果使用sess.close()方法怕会遗漏，也可以在代码前添加``with sess:``，这样在代码写完之后就不用关闭操作。   

### 2.四则运算   

M：tensorflow的加减乘除怎么使用呢？

Z：如下Demo：

```python
import tensorflow as tf
data1 = tf.Variable(6)
data2 = tf.Variable(2)
dataAdd = tf.add(data1, data2)
# 将dataAdd的值赋值到data2上
dataCopy = tf.assign(data2,dataAdd)

dataMul = tf.multiply(data1, data2)
dataSub = tf.subtract(data1, data2)
dataDiv = tf.divide(data1, data2)
init = tf.global_variables_initializer()
sess = tf.Session()
with sess:
    sess.run(init)  # 处理常量
    print(sess.run(dataAdd))
    print(sess.run(dataMul))
    print(sess.run(dataSub))
    print(sess.run(dataDiv))
    print("--------------")
    print(sess.run(dataCopy))  # 输出8
    print(dataCopy.eval())	# 输出14
    print(tf.get_default_session().run(dataCopy))  # 输出20
print('end')
```

输出结果：

```
8
12
4
3.0
--------------
8
14
20
end
```

``dataCopy.eval()``的效果相当于``tf.get_default_session().run(dataCopy)``  

M：那为什么后面的值会是14和20呢？

Z：因为执行``dataCopy.eval()``是要先执行data1 + data2，由于data2已经在上一步被赋值为8，所以输出6+8输出为14。同理后面输出为20

