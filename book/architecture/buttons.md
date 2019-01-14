<!--
# Buttons
-->
# Botões

<!--

---
#### [Clone the code](https://github.com/evancz/elm-architecture-tutorial/) or follow along in the [online editor](https://ellie-app.com/37gVmD7Tm9Ma1).
---

-->
---
#### [Clone o repositório](https://github.com/evancz/elm-architecture-tutorial/) ou siga pelo [editor online](https://ellie-app.com/37gVmD7Tm9Ma1).
---

<!--
Our first example is a simple counter that can be incremented or decremented. I find that it can be helpful to see the entire program in one place, so here it is! We will break it down afterwards.
-->
Nosso primeiro exemplo é um simples contador que pode ser incrementado ou decrementado. Achamos que pode ser útil ter o programa inteiro em apenas um lugar, então aqui está! Veremos depois cada pedaço do programa, passo a passo.


```elm
import Browser
import Html exposing (Html, button, div, text)
import Html.Events exposing (onClick)


main =
  Browser.sandbox { init = init, update = update, view = view }


-- MODEL

type alias Model = Int

init : Model
init =
  0


-- UPDATE

type Msg = Increment | Decrement

update : Msg -> Model -> Model
update msg model =
  case msg of
    Increment ->
      model + 1

    Decrement ->
      model - 1


-- VIEW

view : Model -> Html Msg
view model =
  div []
    [ button [ onClick Decrement ] [ text "-" ]
    , div [] [ text (String.fromInt model) ]
    , button [ onClick Increment ] [ text "+" ]
    ]
```

<!--
That's everything!
-->
Isso é tudo!

<!--
> **Note:** This section has `type` and `type alias` declarations. You can read all about these in the upcoming section on [types](/types/index.html). You do not *need* to deeply understand that stuff now, but you are free to jump ahead if it helps.
-->
> **Observação:** Esta seção contém declarações de `type` e `type alias`. Você pode ler tudo sobre elas na seção de [tipos](/types/index.html). Você não *precisa* entender essas coisas a fundo no momento, mas sinta-se livre para dar uma pulo nesta seção se você achar que vai te ajudar.

<!--
When writing this program from scratch, I always start by taking a guess at the model. To make a counter, we at least need to keep track of a number that is going up and down. So let's just start with that!
-->
Quando escrevemos um programa em Elm, podemos começar tentando adivinhar qual é o `model`, isto é, qual informações precisamos manter e modificar. Para fazer um contador precisamo pelo menos acompanhar um número que vai aumentar e diminuir. Então vamos começar apenas com este número!


```elm
type alias Model = Int
```

<!--
Now that we have a model, we need to define how it changes over time. I always start my `UPDATE` section by defining a set of messages that we will get from the UI:
-->
Agora que temos o `model`, precisamos definiar como ele muda em relação ao tempo. Começaremos a seção de `UPDATE` definindo um grupo de mensagens que vamos receber da UI(interface visual):


```elm
type Msg = Increment | Decrement
```

<!--
I definitely know the user will be able to increment and decrement the counter. The `Msg` type describes these capabilities as *data*. Important! From there, the `update` function just describes what to do when you receive one of these messages.
-->
Sabemos que o usuário poderá incrementar e decrementar o contador. O tipo `Msg` descreve essa capacidade em forma de *dados*. Importante! A função `update` só descreve o que fazer quando recebe uma destas mensagens. 


```elm
update : Msg -> Model -> Model
update msg model =
  case msg of
    Increment ->
      model + 1

    Decrement ->
      model - 1
```

<!--
If you get an `Increment` message, you increment the model. If you get a `Decrement` message, you decrement the model. Pretty straight-forward stuff.
-->
Se você receber a mensagem `Increment`, você incrementa o model. Se você receber uma mensagem `Decrement`, você decrementa o model. Coisas bem simples.

<!--
Okay, so that's all good, but how do we actually make some HTML and show it on screen? Elm has a library called `elm/html` that gives you full access to HTML5 as normal Elm functions:
-->
Certo, então essa parte está feita. Agora, como podemos gerar HTML e mostrá-lo na tela? Elm tem um biblioteca chamada `elm/html` que te dá acesso completo ao HTML5 em forma de funções:


```elm
view : Model -> Html Msg
view model =
  div []
    [ button [ onClick Decrement ] [ text "-" ]
    , div [] [ text (String.fromInt model) ]
    , button [ onClick Increment ] [ text "+" ]
    ]
```

<!--
One thing to notice is that our `view` function is producing a `Html Msg` value. This means that it is a chunk of HTML that can produce `Msg` values. And when you look at the definition, you see the `onClick` attributes are set to give out `Increment` and `Decrement` values. These will get fed directly into our `update` function, driving our whole app forward.
-->
Uma coisa a se observar é que nossa função `view` está produzindo valores `Html Msg`. Isso significa que são valores HTML que podem produzir valores de `Msg`. E quando olhamos na definição, vemos que os atributos `onClick` estão sendo usados com os valores `Increment` e `Decrement`. Estes serão alimentados diretamente à função `update`, movendo nossa aplicação toda adiante.

<!--
Another thing to notice is that `div` and `button` are just normal Elm functions. These functions take (1) a list of attributes and (2) a list of child nodes. It is just HTML with slightly different syntax. Instead of having `<` and `>` everywhere, we have `[` and `]`. We have found that folks who can read HTML have a pretty easy time learning to read this variation. Okay, but why not have it be *exactly* like HTML? **Since we are using normal Elm functions, we have the full power of the Elm programming language to help us build our views!** We can refactor repetitive code out into functions. We can put helpers in modules and import them just like any other code. We can use the same testing frameworks and libraries as any other Elm code. Everything that is nice about programming in Elm is 100% available to help you with your view. No need for a hacked together templating language!
-->
Outra coisa a se notar é que `div` e `button` são apenas funções comuns. Essas funções recebem (1) uma lista de atributos e (2) uma lista de nós filhos. É apenas HTML com uma sintaxe um pouco diferente. Ao invés de ter `<` e `>` para todo lado, nós temos `[` e `]`. Nós percebemos que as pessoas que conseguem ler HTML comum tem facilidade em aprender essa variação. Certo, mas por que não ser *exatamente* igual HTML? **Porque usando funções nó temos o poder completo da linguagem de programação Elm para nos ajudar construir nossas `views`!** Nós podemos refatorar código repetitivo em funções. Podemos colocar funções auxiliares em módulos e importá-las como qualquer outro código. Podemos usar frameworks de teste e bibliotecas como qualquer outro código Elm. Tudo que é bom do Elm está 100% disponível para te ajudar com a sua `view`. Não há necessidade de uma linguagem de _templating_.

<!--
There is also something a bit deeper going on here. **The view code is entirely declarative**. We take in a `Model` and produce some `Html`. That is it. There is no need to mutate the DOM manually. Elm takes care of that behind the scenes. This gives Elm [much more leeway to make optimizations](https://elm-lang.org/blog/blazing-fast-html) and ends up making rendering *faster* overall. So you write less code and the code runs faster. The best kind of abstraction!
-->
Há também outra coisa mais profunda acontecendo aqui. **Nosso código da `view` é totalmente declarativo.** Nós recebemos `Model` e produzimos `Html`. É isso. Não há necessidade de modificar o DOM manualmente. O Elm cuida disso por trás do panos. Isso dá ao Elm [muito mais espaço para fazer otimizações](https://elm-lang.org/blog/blazing-fast-html) e acaba renderizando *mais rápido* de forma geral. Então você escreve menos código e o código roda mais rápido. O melhor tipo de abstração!


<!--
This pattern is the essence of The Elm Architecture. Every example we see from now on will be a slight variation on this basic pattern: `Model`, `update`, `view`.
-->
Esse padrão é a essencia da Arquitetura Elm. Todos os exemplos qu veremos daqui em diante será uma variação deste padrão básico: `Model`, `update` e `view`.


<!--
> **Exercise:** One cool thing about The Elm Architecture is that it is super easy to extend as our product requirements change. Say your product manager has come up with this amazing "reset" feature. A new button that will reset the counter to zero.
>
> To add the feature you come back to the `Msg` type and add another possibility: `Reset`. You then move on to the `update` function and describe what happens when you get that message. Finally you add a button in your view.
>
> See if you can implement the "reset" feature!
-->
> **Exercício:** Uma coisa legal da Arquitetura Elm é que é super fácil de estender quando os requisitos do produto mudam. Digamos que nosso gerente de produto inventou uma funcionalidade _incrível_ de zerar o contador. Um novo botão que redefine o valor do contador para zero.
>
> Para adicionar esta funcionalidade voltamos ao tipo `Msg` e adicionamos outra possibilidade: `Reset`. Vamos então para a função `update` e descrevemos o que acontece quando recebemos essa mensagem. Finalmente, adicionamos o botão na nossa view.
>
> Veja se você consegue implementar essa funcionalidade de zerar o contador!

