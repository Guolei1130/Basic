
思路：拿一个等成数组，去存储最小值的index

```kotlin
object GetMinStackTest {
  @JvmStatic
  fun main(array: Array<String>) {
    val stack = GetMinStack()
    stack.push(2)
    stack.push(4)
    stack.push(1)
    stack.push(5)
    stack.push(7)
    println(stack.getMin())
    println(stack.pop())
  }
}

class GetMinStack {
  var endIndex = -1
  var values = IntArray(16)
  var minIndex = IntArray(16)

  fun push(value: Int) {
    val index = endIndex + 1
    values[index] = value
    if (index == 0) {
      minIndex[index] = 0
    }else {
      minIndex[index] = if (value <= values[minIndex[index - 1]]) index else minIndex[index - 1]
    }
    endIndex++
  }

  fun pop(): Int {
    val value = values[endIndex]
    endIndex--
    return value
  }

  fun getMin(): Int {
    return values[minIndex[endIndex]]
  }

}
```
