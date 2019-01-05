<!--
# An Introduction to Elm
-->
# Introdução ao Elm

<!--
**Elm is a functional language that compiles to JavaScript.** It competes with projects like React as a tool for creating websites and web apps. Elm has a very strong emphasis on simplicity, ease-of-use, and quality tooling.
-->
**Elm é uma linguagem funcional que compila para Javascript.** Ele compete com projetos como o  React para criação de páginas e aplicações web. Elm possui uma forte ênfase em simplicidade, facilidade de uso e qualidade de ferramentas.

<!--
This guide will:

  - Teach you the fundamentals of programming in Elm.
  - Show you how to make interactive apps with *The Elm Architecture*.
  - Emphasize principles and patterns that generalize to programming in any language.
-->
Este guia irá:

  - Ensinar os fundamentos para programar em Elm
  - Mostrar como fazer aplicações interativas  com _A Arquitetura Elm_ (em inglês, *The Elm Architecture*)
  - Enfatizar princípios e padrões que podem ser generalizados para programação em qualquer linguagem.

<!--
By the end I hope you will not only be able to create great web apps in Elm, but also understand the core ideas and patterns that make Elm nice to use.
-->
No final você terá a capacidade de não apenas criar boas aplicações web em Elm, mas também entender as idéias e padrões principais que fazem o Elm ser bom de se utilizar.

<!--
If you are on the fence, I can safely guarantee that if you give Elm a shot and actually make a project in it, you will end up writing better JavaScript and React code. The ideas transfer pretty easily!
-->
Se você está em cima do muro, dê uma chance e utilize Elm num projeto. É muito possível que depois disso você acabe escrevendo um código melhor em Javascript e React. As ideias do que você vai aprender são facilmente reaproveitáveis!

<!--
## A Quick Sample
-->

## Uma Pequena Demonstração

<!--
Of course *I* think Elm is good, so look for yourself.
-->
Claro, o Evan, criador original deste guia e também criador do Elm acha o Elm maravilhoso! Nós também achamos e esperamos que vocês, leitores, também achem! Para isso, a seguir iniciaremos vendo um programa simples em Elm.

<!--
Here is [a simple counter](https://ellie-app.com/new). If you look at the code, it just lets you increment and decrement the counter:
-->
Aqui está [um simples contador](https://ellie-app.com/new). Se você olhar o código, ele permite que você incremente ou decremente o contador:

```elm
import Browser
import Html exposing (Html, button, div, text)
import Html.Events exposing (onClick)

main =
  Browser.sandbox { init = 0, update = update, view = view }

type Msg = Increment | Decrement

update msg model =
  case msg of
    Increment ->
      model + 1

    Decrement ->
      model - 1

view model =
  div []
    [ button [ onClick Decrement ] [ text "-" ]
    , div [] [ text (String.fromInt model) ]
    , button [ onClick Increment ] [ text "+" ]
    ]
```

<!--
Notice that the `update` and `view` are entirely decoupled. You describe your HTML in a declarative way and Elm takes care of messing with the DOM.
-->
Note que o `update` e a `view` são completamente desacoplados. Você escreve seu HTML de uma forma declarativa e o Elm cuida de mexer no DOM.

<!--
## Why a *functional* language?
-->
## Porquê uma linguagem funcional?

<!--
Forget what you have heard about functional programming. Fancy words, weird ideas, bad tooling. Barf. Elm is about:

  - No runtime errors in practice. No `null`. No `undefined` is not a function.
  - Friendly error messages that help you add features more quickly.
  - Well-architected code that *stays* well-architected as your app grows.
  - Automatically enforced semantic versioning for all Elm packages.
-->
Esqueça o que você já escutou sobre programação funcional. Palavras extravagantes, ideias estranhas, ferramentas ruins. Bleh. Elm é sobre:

  - Não há erros em tempo de execução. Não há `null`. Não há `undefined is not a function`.
  - Mensagens de erro amigáveis que ajudam você a implementar funcionalidades mais rapidamente.
  - Código bem arquitetado que *permanece* bem arquitetado conforme seu aplicativo cresce.
  - Versão semântica automaticamente aplicada para todos os pacotes Elm.

<!--
No combination of JS libraries can ever give you this, yet it is all free and easy in Elm. Now these nice things are *only* possible because Elm builds upon 40+ years of work on typed functional languages. So Elm is a functional language because the practical benefits are worth the couple hours you'll spend reading this guide.
-->
Nenhuma combinação de bibliotecas JS pode lhe proporcionar isso, mas é tudo gratuito e fácil em Elm. Agora, essas coisas boas são possíveis *somente* porque Elm se baseia em mais de 40 anos de trabalho de linguagens funcionais tipadas. Então Elm é uma linguagem funcional porque os benefícios práticos valem as horas que você vai gastar lendo este guia.

<!--
I have put a huge emphasis on making Elm easy to learn and use, so all I ask is that you give Elm a shot and see what you think. I hope you will be pleasantly surprised!
-->
Como o autor Evan está fazendo um grande esforço para você aprender facilmente Elm e começar a usá-lo, por favor, dê uma chance ao Elm e veja o que acha.
(Em português, nós temos o grupo de telegram [Elm Brasil](https://t.me/elmbrasil), junte-se a nós e conte-nos qual a sua impressão da linguagem).

Espero que Elm te surpreenda positivamente!
