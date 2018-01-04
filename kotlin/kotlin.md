# kotlinの文法

```kotlin
fun main(args: Array<String>){
	val hello: String = "hello" //final String hello = "hello"と同じ意味
	var world = "world" //Stirng world = "world"と同じ意味。自動型推論
	var num: Int = 5; //プリミティブ型でも先頭大文字。クラスとして振る舞うため、メソッドも呼べる
	

	//for
	for(i in 0 util num){
		print(i.toString() + ": ")
		println(hello + ", " + world) //System.out.println(hello + ", " + world);と同じ意味
	}

	//switch
	for(i in 0..num){
		val str = when(i){
			0 -> "zero"
			1, 2, 3 -> "num"
			else -> "finish"
		}
		println(str)
	}

	//クラスの生成、使用
	val person = Person("Edward", "Elric") //new Person("Edward", "Elric", 0);と同じ
	println(person.fullName)

	person.age = age + 1
}


class Person(val firstName: String, val lastName: String, var age: Int = 0){
	var array = intArrayOf(1, 2, 3)

	//どちらも同じ意味(内容は変えてある)
	val fullName: String
		get() = firstName + "" lastName
	val fullNameR: String
		get(){
			return lastName + "" + firstName
		}

}
```
