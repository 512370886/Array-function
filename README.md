# Array-function
Array方法的总结

* 1.toString: 返回以数组中的每个值的字符串形式拼接而成的一个以逗号分割的字符串

    ```
        toStringArr = [1, 2, 3, 4, 5, 6]
console.log(toStringArr.toString())
// -> 1,2,3,4,5,6
    ```
***
* 2.valueOf: 返回数组对象的原始值。返回的还是数组  

    ```
    valueOfArr = [1, 2, 3, 4, 5, 6]
console.log(valueOfArr.valueOf())
// -> [1, 2, 3, 4, 5, 6]
    ```
***
* 3.join: 通过指定的分隔符进行分隔并返回一个字符串

    ```
    var arr = [1, 2, 3, 4, 5, 6]
var joinArr = arr.join('&')
console.log('join:' + joinArr)
// -> join:1&2&3&4&5&6
    ```
***
* 4.push: 向数组的末尾添加一个或更多元素，并返回新的长度

    ```
    var pushArr = [1, 2, 3, 4, 5, 6]
pushArr.push(7)
console.log(pushArr)
// -> [1, 2, 3, 4, 5, 6, 7]
    ```
***
* 5.pop: 删除数组的最后一个元素并返回删除的元素, 如果数组为空就返回undefined

    ```
    var popArr = [1, 2, 3, 4, 5, 6]
var popEle = popArr.pop()
console.log(popEle, popArr)
// -> 6,  [1, 2, 3, 4, 5]
    
    ```
***
* 6.shift: 删除并返回数组的第一个元素, 如果数组为空，则shift() 方法不进行任何操作，返回undefined

    ```
    var shiftArr = [1, 2, 3, 4, 5, 6]
var shiftEle = shiftArr.shift()
console.log(shiftEle, shiftArr)
// -> 1,  [2, 3, 4, 5, 6]
    ```
***
* 7.unshift: 向数组的开头添加一个或更多元素，并返回新的长度

    ```
    var unshiftArr = [1, 2, 3, 4, 5, 6]
unshiftArr.unshift(0)
console.log(unshiftArr)
// -> [0, 1, 2, 3, 4, 5, 6]
    
    ```
***

* 8.reverse: 反转数组的元素顺序

    ```
    var reverseArr = [1, 2, 3, 4, 5, 6]
reverseArr.reverse()
console.log(reverseArr)
// -> [6, 5, 4, 3, 2, 1]    
    ```
***
* 9.sort: 对数组的元素进行排序

    ```
    // a. 
        var sortArr1 = [1, 3, 5, 2, 7, 6]
        sortArr1.sort()
        console.log(sortArr1)
        // -> [1, 2, 3, 5, 6, 7]
    // b.  因为sort排序是从左至右比较，只要其中一个比较出了结果，就直接返
        var sortArr2 = [1, 3, 19, 5, 17, 6]
        sortArr2.sort()
        console.log(sortArr2)
        // -> [1, 17, 19, 3, 5, 6]
    // c: 封装sort
        function sort(arr, type) {
            type = type || 1
            return arr.sort( (a, b) => {
                switch(type) {
                    case 1: // 从小到大
                        return a - b
                    case 2: // 从大到小
                        return b - a
                    case 3: // 随机排序
                        return Math.random() - 0.5
                    default:
                        return arr
                }
            })
        }
        var sortArr3 = [1, 3, 19, 5, 17, 6]
        sort(sortArr3)
        console.log(sortArr3)
    ```
***
* 10.concat：连接两个或更多的数组，并返回结果

    ```
    var concat1 = [1, 2, 3],
    concat2 = [4, 5, 6]
concatArr = concat1.concat(concat2)
console.log(concatArr)
// -> [1, 2, 3, 4, 5, 6]
    ```
***
* 11.slice(start, end): 选取数组的的一部分，并返回一个新数组, start必须，end可选

    ```
    var sliceArr = [1, 2, 3, 4, 5, 6]
var sliceNewArr = sliceArr.slice(1, -1) // 截取第二个 到 倒数第二个
console.log(sliceNewArr)
// -> [2, 3, 4, 5]
    ```
***
* 12.splice(index, howmany, item1,.....,itemX): 从数组中添加或删除元素

    ```
    /*
        index:  必需。规定从何处添加/删除元素。 该参数是开始插入和（或）删除的数组元素的下标，必须是数字
        howmany: 必需。规定应该删除多少元素。必须是数字，但可以是 "0"。 如果未规定此参数，则删除从 index 开始到原数组结尾的所有元素。
        item1,.....,itemX: 可选。要添加到数组的新元素
    */
    var spliceArr1 = [1, 2, 3, 4, 5, 6]
    spliceArr1.splice(2, 2, 10, 12) // 从下标为2 的地方开始删除 后面的两个元素， 并在这个地方插入 10,12两个元素 
    console.log(spliceArr1)
    // -> [1, 2, 10, 12, 5, 6]
    
    var spliceArr = [1, 2, 3, 4, 5, 6]
    spliceArr.splice(2, 0, 10, 12) // 当需要删除的元素为0， 相当于在这个位置插入元素
    console.log(spliceArr)
    // -> [1, 2, 10, 12, 3, 4, 5, 6]    
    ```
***
* 13.copyWithin(target, start, end): 从数组的指定位置拷贝元素到数组的另一个指定位置中

    ```
    /*
        target: 必需。复制到指定目标索引位置。
        start: 必需。元素复制的起始位置。
        end: 可选。停止复制的索引位置 (默认为 array.length)
    */
var copyWithinArr = [1, 2, 3, 4, 5, 6]
copyWithinArr.copyWithin(1, 2, 4)
console.log(copyWithinArr)
// -> [1, 3, 4, 4, 5, 6]
    ```
***
* 14.fill(value, start, end): 用于将一个固定值替换数组的元素

    ```
    /*
        value: 必需。填充的值。
        start: 可选。开始填充位置。
        end: 可选。停止填充位置 (默认为 array.length)
    */
var fillArr = [1, 2, 3, 4, 5, 6]
fillArr.fill(9, 2, 4)
console.log(fillArr)
// -> [1, 2, 9, 9, 5, 6]
    ```
***
* 15.includes(searchElement, fromIndex)：用来判断一个数组是否包含一个指定的值，如果是返回 true，否则false

    ```
    var includesArr = [1, 2, 3, 4, 5, 6]
var includes1 = includesArr.includes(3)
var includes2 = includesArr.includes(10)
console.log(includes1, includes2)
// -> true, false   
    ```
***
* 16.indexOf(item,start)：可返回某个指定的字符串值在字符串中首次出现的位置

    ```
    var indexOfArr = [1, 2, 3, 4, 3, 6]
var indexOfEle = indexOfArr.indexOf(3)
console.log(indexOfEle)
// -> 2 
    ```
***
* 17.lastIndexOf(item,start)：返回一个指定的字符串值最后出现的位置，在一个字符串中的指定位置从后向前搜索

    ```
var lastIndexOfArr = [1, 2, 3, 4, 3, 6]
var lastIndexOfEle = lastIndexOfArr.lastIndexOf(3)
console.log(lastIndexOfEle)
// -> 4     
    ```
***
* 18.find(function(currentValue, index, arr),thisValue):  返回传入一个测试条件（函数）符合条件的数组第一个元素

    ```
    /*  
        function(currentValue, index, arr):
            a. currentValue: 必需。当前元素
            b. index: 可选。当前元素的索引值
            c. arr: 可选。当前元素所属的数组对象
        thisValue: 可选。 传递给函数的值一般用 "this" 值。 如果这个参数为空， "undefined" 会传递给 "this" 值
        
    */
var findArr = [1, 2, 3, 4, 5, 6]
var findEle = findArr.find( function(currentValue, index, arr) {
    return currentValue >= 4
})
console.log(findEle)
    
    ```
***
* 19.findIndex(function(currentValue, index, arr),thisValue):  返回符合测试条件的第一个数组元素索引，如果没有符合条件的则返回 -1

    ```
    /*  
        function(currentValue, index, arr):
            a. currentValue: 必需。当前元素
            b. index: 可选。当前元素的索引值
            c. arr: 可选。当前元素所属的数组对象
        thisValue: 可选。 传递给函数的值一般用 "this" 值。 如果这个参数为空， "undefined" 会传递给 "this" 值
        
    */
var findIndexArr = [1, 2, 3, 4, 5, 6]
var findIndexEle = findIndexArr.findIndex( function(currentValue, index, arr) {
    return currentValue >= 4
})
console.log(findIndexEle)   
    ```
***
* 20.forEach(function(currentValue, index, arr), thisValue): 用于调用数组的每个元素，并将元素传递给回调函数。没有返回值

    ```
    /*  
        function(currentValue, index, arr):
            a. currentValue: 必需。当前元素
            b. index: 可选。当前元素的索引值
            c. arr: 可选。当前元素所属的数组对象
        thisValue: 可选。 传递给函数的值一般用 "this" 值。 如果这个参数为空， "undefined" 会传递给 "this" 值
        
    */
var forEachArr = [1, 2, 3, 4, 5, 6]
forEachArr.forEach( function(currentValue, index, arr){
    console.log(currentValue)
})
// -> 依次打印 1 2 3 4 5 6, 没有返回值   
    ```
***
* 21.map(function(currentValue, index, arr), thisValue): 返回一个新数组，数组中的元素为原始数组元素调用函数处理后的值

    ```
    /*  
        function(currentValue, index, arr):
            a. currentValue: 必需。当前元素
            b. index: 可选。当前元素的索引值
            c. arr: 可选。当前元素所属的数组对象
        thisValue: 可选。 传递给函数的值一般用 "this" 值。 如果这个参数为空， "undefined" 会传递给 "this" 值
        
    */
var mapArr = [1, 2, 3, 4, 5, 6]
var mapNewArr = mapArr.map( function(currentValue, index, arr){
    // console.log(currentValue)
    return currentValue*2
})
console.log(mapNewArr)
// -> [2, 4, 6, 8, 10, 12]
    
    ```
***
* 22.reduce(function(total, currentValue, index, arr), thisValue): 接收一个函数作为累加器，数组中的每个值（从左到右）开始缩减，最终计算为一个值

    ```
    /*  
        function(currentValue, index, arr):
            a. currentValue: 必需。当前元素
            b. index: 可选。当前元素的索引值
            c. arr: 可选。当前元素所属的数组对象
            d: total:   必需。初始值, 或者计算结束后的返回值。
        thisValue: 可选。 传递给函数的值一般用 "this" 值。 如果这个参数为空， "undefined" 会传递给 "this" 值
        
    */
var reduceArr = [1, 2, 3, 4, 5, 6]
var reduceNewArr = reduceArr.reduce( function(total, currentValue, index, arr){
    return total - currentValue
})
console.log(reduceNewArr)
// -> 19    
    ```
***
* 23.reduceRight(function(total, currentValue, index, arr), thisValue): 接收一个函数作为累加器，数组中的每个值（从右到左）开始缩减，最终计算为一个值

    ```
    /*  
        function(currentValue, index, arr):
            a. currentValue: 必需。当前元素
            b. index: 可选。当前元素的索引值
            c. arr: 可选。当前元素所属的数组对象
            d: total:   必需。初始值, 或者计算结束后的返回值。
        thisValue: 可选。 传递给函数的值一般用 "this" 值。 如果这个参数为空， "undefined" 会传递给 "this" 值
        
    */
var reduceRightArr = [1, 2, 3, 4, 5, 6]
var reduceRightNewArr = reduceRightArr.reduceRight( function(total, currentValue, index, arr){
    return total - currentValue
})
console.log(reduceRightNewArr)
// -> -9    
    ```
***
* 24.some(function(currentValue, index, arr), thisValue): 如果有一个元素满足条件，则表达式返回true , 剩余的元素不会再执行检测。如果没有满足条件的元素，则返回false

    ```
    /*  
        function(currentValue, index, arr):
            a. currentValue: 必需。当前元素
            b. index: 可选。当前元素的索引值
            c. arr: 可选。当前元素所属的数组对象
        thisValue: 可选。 传递给函数的值一般用 "this" 值。 如果这个参数为空， "undefined" 会传递给 "this" 值
        
    */
var someArr = [1, 2, 3, 4, 5, 6]
var someEle1 = someArr.some( function(currentValue, index, arr){
    return currentValue > 4
})
var someEle2 = someArr.some( function(currentValue, index, arr){
    return currentValue > 6
})
console.log(someEle1, someEle2)
// -> true, false   
    ```
***
* 25.every(function(currentValue, index, arr), thisValue): 如果数组中检测到有一个元素不满足，则整个表达式返回 false ，且剩余的元素不会再进行检测。如果所有元素都满足条件，则返回 true

    ```
    /*  
        function(currentValue, index, arr):
            a. currentValue: 必需。当前元素
            b. index: 可选。当前元素的索引值
            c. arr: 可选。当前元素所属的数组对象
        thisValue: 可选。 传递给函数的值一般用 "this" 值。 如果这个参数为空， "undefined" 会传递给 "this" 值
        
    */
var everyArr = [1, 2, 3, 4, 5, 6]
var everyEle1 = everyArr.every( function(currentValue, index, arr){
    return currentValue > 0
})
var everyEle2 = everyArr.every( function(currentValue, index, arr){
    return currentValue > 1
})
console.log(everyEle1, everyEle2)
// -> true, false   
    ```
***
* 26.filter(function(currentValue, index, arr), thisValue):创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素

    ```
    /*  
        function(currentValue, index, arr):
            a. currentValue: 必需。当前元素
            b. index: 可选。当前元素的索引值
            c. arr: 可选。当前元素所属的数组对象
        thisValue: 可选。 传递给函数的值一般用 "this" 值。 如果这个参数为空， "undefined" 会传递给 "this" 值
        
    */
var filterArr = [1, 2, 3, 4, 5, 6]
var filterNewArr = filterArr.filter( function(currentValue, index, arr){
    return currentValue > 2
})
console.log(filterNewArr)
// -> [3, 4, 5, 6]  
    ```
***
* 27.from: 将类数组对象和可遍历对象转化为数组

    ```
    fromObj = {
  0: '0',
  1: '1',
  3: '3',
  length:4
}
arrayArr = Array.from(fromObj)
console.log(arrayArr)
// -> ["0", "1", undefined, "3"]    
    ```
***
* 28.of: 创建一个具有可变数量参数的新数组实例，而不考虑参数的数量或类型

```
    Array.of(7);       // -> [7] 
    Array.of(1, 2, 3); // -> [1, 2, 3]

    Array(7);          // -> [ , , , , , , ]
    Array(1, 2, 3);    // -> [1, 2, 3]  
```
***

