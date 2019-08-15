```kotlin
fun kNode(headerNode: LinkNode<Any>?, k: Int): LinkNode<Any>? {
  if (headerNode == null || k < 0) return null

  var quick = headerNode
  var slow = headerNode
  for (i in 0 until k) {
    if (quick!!.next != null) {
      quick = quick.next
    }else {
      return null
    }
  }
  while (quick!!.next != null) {
    quick = quick.next
    slow = slow!!.next
  }
  return slow
}
```
