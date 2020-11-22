# Set

## §3. Methods and properties

Возможно, не стоит демонстрировать `isEmpty`/`size`/... внутри строк, а давать новым переменным имена:

```diff
val visitors = setOf("Paula", "Tanya", "Julia")

- println("Is it true that Tanya came? It's ${visitors.contains("Tanya")}") // Is it true that Tanya came? It's true
+ val isTanyaInCafe = visitors.contains("Tanya") 
+ println("Is it true that Tanya came? It's $isTanyaInCafe") // Is it true that Tanya came? It's true

+ val indexOfTanya = visitors.indexOf("Tanya")
- println("And what is her index? $indexOfTanya" ) // And her index is 1
```

> If you want to add two sets together simply use the "+" operator, or "-" operator if you want to subtract one from the other.

Можно добавить во второе множество уникальный элемент:
``` diff
val productsList1 = setOf("Banana", "Lime", "Strawberry")
- val productsList2 = setOf("Strawberry")
+ val productsList2 = setOf("Lemon", "Strawberry")

val finalProductsList1 = productsList1 + productsList2
println(finalProductsList1) // [Banana, Lime, Lemon, Strawberry]

val finalProductsList2 = productsList1 - productsList2
println(finalProductsList2) // [Banana, Lime]
```

> Got an Array and want to convert it to Set? Not a big deal, use toSet()method:

"... и в нём гарантированно не будет дубликатов".
