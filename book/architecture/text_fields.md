<!--
# Text Fields
-->
# Caixa de texto

<!--

---
#### [Clone the code](https://github.com/evancz/elm-architecture-tutorial/) or follow along in the [online editor](https://ellie-app.com/37gW7sj9wPVa1).
---
-->
---
#### [Clone o repositório](https://github.com/evancz/elm-architecture-tutorial/) ou siga no [editor online](https://ellie-app.com/37gW7sj9wPVa1).
---

<!--
We are about to create a simple app that reverses the contents of a text field.
-->
Em seguida criaremos uma aplicação web que inverte o conteúdo de uma caixa de texto.

<!--
Again this is a pretty short program, so I have included the whole thing here. Skim through to get an idea of how everything fits together. Right after that we will get into the details!
-->
Novamente é um programa curto, então incluímos ele inteiro abaixo. Dê uma olhada no código para ter uma idéia de como as coisas funcionam. Logo na sequência entraremos nos detalhes de cada pedaço!




```elm
import Browser
import Html exposing (Html, Attribute, div, input, text)
import Html.Attributes exposing (..)
import Html.Events exposing (onInput)



-- MAIN


main =
  Browser.sandbox { init = init, update = update, view = view }



-- MODEL


type alias Model =
  { content : String
  }


init : Model
init =
  { content = "" }



-- UPDATE


type Msg
  = Change String


update : Msg -> Model -> Model
update msg model =
  case msg of
    Change newContent ->
      { model | content = newContent }



-- VIEW


view : Model -> Html Msg
view model =
  div []
    [ input [ placeholder "Text to reverse", value model.content, onInput Change ] []
    , div [] [ text (String.reverse model.content) ]
    ]
```

<!--
This code is a slight variant of the counter from the previous section. You set up a model. You define some messages. You say how to `update`. You make your `view`. The difference is just in how we filled this skeleton in. Let's walk through that!
-->
Este código é uma pequena variação do contador da seção anterior. Preparamos um `model`. Definimos algumas mensagens. Dizemos como fazer o `update`. Fazemos a `view`. A diferença é apenas em como nós preenchemos esse _esqueleto_. Vamos analisar passo a passo!

<!--
As always, you start by guessing at what your `Model` should be. In our case, we know we are going to have to keep track of whatever the user has typed into the text field. We need that information so we know how to render the reversed text.
-->
Como de costume, começamos tentando adivinhar o que nosso `model` deveria ser. Neste caso, sabemos que teremos que acompanhar o que o usuário digitar na caixa de texto. Precisaremos deste informação para saber como mostrar o texto invertido.


```elm
type alias Model =
  { content : String
  }
```

<!--
This time I chose to represent the model as a record. (You can read more about records [here](https://guide.elm-lang.org/core_language.html#records) and [here](https://elm-lang.org/docs/records).) For now, the record stores the user input in the `content` field.
-->
Deste vez escolhemos representar o modelo como um _registro_. (Você pode ler mais sobre registros [aqui](https://guia.elm-lang.pt/core_language.html#records) and [aqui](https://elm-lang.org/docs/records).) Por enquanto, o registro contém apenas o texto digitado no campo `content`.

<!--
> **Note:** You may be wondering, why bother having a record if it only holds one entry? Couldn't you just use the string directly? Sure! But starting with a record makes it easy to add more fields as our app gets more complicated. When the time comes where we want *two* text inputs, we will have to do much less fiddling around.
-->
> **Observação:** Você pode estar se perguntando, pra quê ter um registro se ele só contém uma entrada? Não poderíamos usar uma `String` diretamente? Certamente! Mas começar com um registro facilita adicionar mais campos conforme nossa aplicação vai ficando mais complexa. Quando chegar o momento que queremos *duas* caixas de texto, teremos muito menos trabalho.

<!--
Okay, so we have our model. Now in this app there is only one kind of message really. The user can change the contents of the text field.
-->
Certo, então temos nosso _model_. Agora, nesta aplicação temos apenas um tipo de mensagem. O usuário pode apenas mudar o conteúdo da caixa de texto.


```elm
type Msg
  = Change String
```

<!--
This means our update function just has to handle this one case:
-->
Isso quer dizer que nossa função _update_ precisa lidar apenas com esse único caso:


```elm
update : Msg -> Model -> Model
update msg model =
  case msg of
    Change newContent ->
      { model | content = newContent }
```

<!--
When we receive new content, we use the record update syntax to update the contents of `content`.
-->
Quando recebermos um novo conteúdo, usamos a sintaxe de atualizar registro para atualizar o conteúdo de `content`.

<!--
Finally we need to say how to view our application:
-->
Por fim, preciamos definiar a `view` para visualizarmos nossa aplicação:


```elm
view : Model -> Html Msg
view model =
  div []
    [ input [ placeholder "Text to reverse", value model.content, onInput Change ] []
    , div [] [ text (String.reverse model.content) ]
    ]
```

<!--
We create a `<div>` with two children.
-->
Criamos uma `<div>` com dois nós filhos.

<!--
The interesting child is the `<input>` node. In addition to the `placeholder` and `value` attributes, it uses `onInput` to declare what messages should be sent when the user types into this input.
-->
O filho interessante é o nó `<input>`. Além dos atributos `placeholder` e `value`, ele usa `onInput` para declarar qual mensagem deve ser enviada quando o usuário digita nesta caixa de texto.

<!--
This `onInput` function is kind of interesting. It takes one argument, in this case the `Change` function which was created when we declared the `Msg` type:
-->
Esta função `onInput` é interessante. Ela recebe um argumento, que neste caso é a função `Change` que foi criada quando declaramos o tipo `Msg`:


```elm
Change : String -> Msg
```

<!--
This function is used to tag whatever is currently in the text field. So let's say the text field currently holds `glad` and the user types `e`. This triggers an `input` event, so we will get the message `Change "glade"` in our `update` function.
-->
Este função é usada para sinalizar qual o conteúdo atual da caixa de texto. Digamos que a caixa de texto atualmente contém `glad` e o usuário digitou `e`. Isso desencadeia um evento `input`, então o que receberam a mensagem `Change "glade"` na nossa função `update`.

<!--
So now we have a simple text field that can reverse user input. Neat! Now on to putting a bunch of text fields together into a more traditional form.
-->
Então agora temos uma simples caixa de texto que pode inverter o que é digitado. Bacana! Agora vamos partir para colocar alguns textos em um formulário mais tradicional.

