Примечание: к большинству замечаний можно приставить в начале "мне кажется" (особенно стилистических).

# Theory: String arrays 

## §1. Initialization

> Kotlin does not provide a special function to create an array of strings, so you need to use the function arrayOf which is already familiar to you.

Такая формулировка (нет специальной функции для массива строк, используйте функцию для создания массива) может запутать. Достаточно сказать, что массивы в Котлине создаются с помощью `arrayOf()` и если передать внутрь только строку — компилятор умный и выведет правильный тип.

> You can also initialize an empty array to be filled with strings later. For this, you need the function emptyArray:

Что не совсем так, поскольку операция `+` будет создавать новый массив большего размера, но не изменять текущий. Полагаю, лучше вообще упустить упоминание "to be filled with strings later".

## §2. Accessing elements

> Since everything you already know about arrays still applies, you can access a certain element by its index:

Формулировка кажется немного сложной для понимания. Но это субъективно.

## §4. Working with multiple arrays

> You can concatenate several arrays as shown in the following example:

Можно явно продемонстрировать возможность дублирования элементов:
```
val southernCross = arrayOf("Acrux", "Gacrux", "Imai", "Mimosa")
val stars = arrayOf("Ginan", "Imai")

val newArray = southernCross + stars
println(newArray.joinToString())    //  Acrux, Gacrux, Imai, Mimosa, Ginan, Imai
```

Возможно, где-то в самом верху стоит указать, что по историческим причинам, массивы в Kotlin следует использовать только в исключительных случаях, когда точно известно, что нужен именно массив (например, для тонких оптимизаций или совместимости с Java кодом). В остальных случаях следует использовать списки — это более канонично и безопасно.

> You cannot use the operators == and != to compare arrays because they simply do not compare their contents. With arrays, use the function contentEquals() instead:

Возможно, стоит добавить, что `==` в случае с массивами будет сравнивать их размещение в памяти, а не контент. Некоторые вещи вынуждено переехали в Котлин из языка Java или из-за особенностей платформы JVM. У изучающих может сложится впечатление, что язык хаотичен и непоследовательный (везде используем `==`, а тут зачем-то `contentEquals()`), если ему не говорить об исторической природе таких вот исключений.

Также в этом абзаце можно продемонстрировать и `==`:
```diff

+ println(firstArray == secondArray)	// false
println(firstArray.contentEquals(secondArray))  //  true
```

и сравнение одинакового контента с различной последовательностью:
```
val forward = arrayOf("mike", "nick")
val backward = arrayOf("nick", "mike")
forward.contentEquals(backward)	// false
```

## §5. Changing the array contents

> No matter if you're using val or var, you can edit the values of the existing elements through their index:

Не уверен, что `val/var` следует упоминать тут. Или делать это, объяснив, что `val/var` не имеет никакого отношения к контенту объектов/массивов.

> However, there is a great difference between val and var when it comes to reassignment. When you have a var array, you can change it by adding new elements to it.

Не хватает демонстрации того, как работает `+` (создаёт новый массив).

```
val arr = arrayOf("one")

val arr2 = arr + "two"

println(arr.joinToString())		// one
println(arr2.joinToString())	// one, two
```

Отсюда проще объяснить что такое `+=` и почему для его использования нельзя использовать `val` (что, впрочем, рассказано ниже).
