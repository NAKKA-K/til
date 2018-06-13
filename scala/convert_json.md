## Jsonへの変換方法(Scalaのデータ -> Json)
`post.get("ID")`などから返る値はOption[Any]型なので、それぞれStringなど指定した型に変換する必要がある。  
`post.get("ID").toString`で返る値は、Some(a2b......)やNoneといった形で値が返る。  
Some()から値を取り出すには、getメソッドを適応するかmatchを使う必要がある。  
getで取得した場合、Errorが出る場合もあるので、matchで扱うのが良い。  
今回はmatch用の関数を定義して適応している。  
関数では戻り値の型を指定しないとUnit型が返るので、StringやIntなど個別の関数を用意した。  

writesは実のところ簡素にかけるメソッドがあり、以下の方法は複雑なJSONを適応するときなどに使用する。(簡易な書き方は以下に別コメントとして追記する)  

```scala
implicit val postWrites = new Writes[Post] {
  def writes(post: Post) = Json.obj(
    "id" -> post.id,
    "user_id" -> post.user_id,
    "text" -> post.text,
    "parent_post_id" -> post.parent_post_id,
    "comment_count" -> post.comment_count,
    "posted_at" -> post.posted_at
  )
}

val json = Json.toJson(Post(
  getStringValue(post.get("ID")),
  getStringValue(post.get("USER_ID")),
  getStringValue(post.get("TEXT")),
  getStringValue(post.get("PARENT_POST_ID")),
  getIntValue(post.get("COMMENT_COUNT")),
  getStringValue(post.get("POSTED_AT"))
))

def getStringValue(o: Option[Any]): String = {
  o match {
    case Some(x: String) => x
    case Some(x)         => x.toString
    case None            => null
  }
}

def getIntValue(o: Option[Any]): Int = {
  o match {
    case Some(x: Int) => x
  }
}

case class Post(
    id: String,
    user_id: String,
    text: String,
    parent_post_id: String,
    comment_count: Int,
    posted_at: String
)
```
