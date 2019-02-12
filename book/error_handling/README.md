<!-- # Error Handling

One of the guarantees of Elm is that you will not see runtime errors in practice. This is partly because **Elm treats errors as data**. Rather than crashing, we model the possibility of failure explicitly with custom types. For example, say you want to turn user input into a age. You might create a custom type like this:

-->

# Tratamento de erros

Uma das garantias do Elm, é que você não verá erros de execução na prática. Isto é em parte porque o **Elm trata os erros como dados**. Em vez de travar, modelamos a possibilidade de falha explicitamente com tipos personalizados. Por exemplo, digamos que você queira transformar a entrada do usuário em uma idade. Você pode criar um tipo personalizado como este:

<!-- 
```elm
type MaybeAge
  = Age Int
  | InvalidInput

toAge : String -> MaybeAge
toAge userInput =
  ...

-- toAge "24" == Age 24
-- toAge "99" == Age 99
-- toAge "ZZ" == InvalidInput
```
-->

```elm
type MaybeAge
  = Age Int
  | InvalidInput

toAge : String -> MaybeAge
toAge userInput =
  ...

-- toAge "24" == Age 24
-- toAge "99" == Age 99
-- toAge "ZZ" == InvalidInput
```

<!-- Instead of crashing on bad input, we say explicitly that the result may be an `Age 24` or an `InvalidInput`. No matter what input we get, we always produce one of these two variants. From there, we use pattern matching which will ensure that both possibilities are accounted for. No crashing! -->

Em vez de travar com entrada incorreta, dizemos explicitamente que o resultado pode ser um "Age 24" ou um "InvalidInput". Não importa qual entrada recebemos, sempre produzimos uma dessas duas variantes. A partir daí, usamos a correspondência de padrões que garantirá que ambas as possibilidades sejam consideradas. Sem quebrar!

<!-- This kind of thing comes up all the time! For example, maybe you want to turn a bunch of user input into a `Post` to share with others. But what happens if they forget to add a title? Or there is no content in the post? We could model all these problems explicitly: -->

Esse tipo de coisa surge o tempo todo! Por exemplo, talvez você queira transformar um monte de entradas do usuário em um "Post" para compartilhar com os outros. Mas o que acontece se eles se esquecerem de adicionar um título? Ou não há conteúdo no post? Nós poderíamos modelar todos esses problemas explicitamente:

<!-- ```
type MaybePost
  = Post { title : String, content : String }
  | NoTitle
  | NoContent

toPost : String -> String -> MaybePost
toPost title content =
  ...

-- toPost "hi" "sup?" == Post { title = "hi", content = "sup?" }
-- toPost ""   ""     == NoTitle
-- toPost "hi" ""     == NoContent
``` -->

```
type MaybePost
  = Post { title : String, content : String }
  | NoTitle
  | NoContent

toPost : String -> String -> MaybePost
toPost title content =
  ...

-- toPost "hi" "sup?" == Post { title = "hi", content = "sup?" }
-- toPost ""   ""     == NoTitle
-- toPost "hi" ""     == NoContent
```

<!-- Instead of just saying that the input is invalid, we are describing each of the ways things might have gone wrong. If we have a `viewPreview : MaybePost -> Html msg` function to preview valid posts, now we can give more specific error messages in the preview area when something goes wrong! -->

Em vez de apenas dizer que a entrada é inválida, estamos descrevendo cada uma das maneiras pelas quais as coisas podem ter dado errado. Se tivermos uma função `viewPreview: MaybePost -> Html msg` para visualizar postagens válidas, agora podemos fornecer mensagens de erro mais específicas na área de visualização quando algo der errado!

<!-- These kinds of situations are extremely common. It is often valuable to create a custom type for your exact situation, but in some of the simpler cases, you can use an off-the-shelf type instead. So the rest of this chapter explores the `Maybe` and `Result` types, showing how they can help you treat errors as data! -->

Esses tipos de situações são extremamente comuns. Muitas vezes, é importante criar um tipo personalizado para sua situação exata, mas, em alguns casos mais simples, é possível usar um tipo pronto para uso. Então o resto deste capítulo explora os tipos `Maybe` e` Result`, mostrando como eles podem ajudá-lo a tratar os erros como dados!
