<!--
# The Elm Architecture
-->

# A Arquitetura Elm 

<!--
The Elm Architecture is a simple pattern for architecting webapps. It is great for modularity, code reuse, and testing. Ultimately, it makes it easy to create complex web apps that stay healthy as you refactor and add features.
-->

A Arquitetura Elm é um padrão simples para arquitetar aplicações web. É ótimo para modularização, reutilização de código, e teste. Fundamentalmente, ele facilita a criação de aplicações complexas que se mantem saudáveis quando refatoradas e quando novas funcionalidades são adicionadas.

<!--
This architecture seems to emerge naturally in Elm. Rather than someone “inventing” it, early Elm programmers kept discovering the same basic patterns in their code. Teams have found this particularly nice for onboarding new developers. Code just turns out well-architected. It is kind of spooky.
-->

Esta arquitetura parece emergir naturalmente em Elm. Em vez de alguém “inventá-la”, os programadores Elm acabaram descobrindo os mesmos padrões básicos em seu código. As equipes acharam isso particularmente interessante para integrar novos(as) desenvolvedores(as). O código acaba bem arquitetado. É até meio assustador.

<!--
So The Elm Architecture is *easy* in Elm, but it is useful in any front-end project. In fact, projects like Redux have been inspired by The Elm Architecture, so you may have already seen derivatives of this pattern. Point is, even if you ultimately cannot use Elm at work yet, you will get a lot out of using Elm and internalizing this pattern.
-->

Então, A Arquitetura Elm é *fácil* em Elm, mas é útil em qualquer projeto de front-end. Na verdade, projetos como o Redux foram inspirados pela Arquitetura Elm, então você já deve ter visto derivados desse padrão. O ponto é que, mesmo que você ainda não possa usar Elm no trabalho, você se beneficiará muito por utilizar Elm e internalizar esse padrão.

[Elm]: https://elm-lang.org/
[TodoMVC]: https://github.com/evancz/elm-todomvc
[dreamwriter]: https://github.com/rtfeldman/dreamwriter#dreamwriter
[NoRedInk]: https://www.noredink.com/
[CircuitHub]: https://www.circuithub.com/
[Pivotal]: https://www.pivotaltracker.com/blog/Elm-pivotal-tracker/


<!--
## The Basic Pattern
-->

## O Padrão Básico

<!--
The logic of every Elm program will break up into three cleanly separated parts:
-->

A lógica de todo programa Elm se dividirá em três partes separadas:

<!--
  * **Model** &mdash; the state of your application
  * **Update** &mdash; a way to update your state
  * **View** &mdash; a way to view your state as HTML
-->

  * **Model** &mdash; o estado da nossa aplicação
  * **Update** &mdash; um jeito de atualizar o estado
  * **View** &mdash; uma forma de ver o estado no HTML

<!--
This pattern is so reliable that I always start with the following skeleton and fill in details for my particular case.
-->

Esse padrão é tão confiável que sempre começo com o seguinte esqueleto e preencho detalhes para o meu caso particular.

```elm
import Html exposing (..)


-- MODEL

type alias Model = { ... }


-- UPDATE

type Msg = Reset | ...

update : Msg -> Model -> Model
update msg model =
  case msg of
    Reset -> ...
    ...


-- VIEW

view : Model -> Html Msg
view model =
  ...
```

<!--
That is really the essence of The Elm Architecture! We will proceed by filling in this skeleton with increasingly interesting logic.
-->

Essa é realmente a essência da Arquitetura Elm! Continuaremos preenchendo esse esqueleto com uma lógica cada vez mais interessante.


<!--
# The Elm Architecture + User Input
-->

# A arquitetura do Elm + Entrada do usuário

<!--
Your web app is going to need to deal with user input. This section will get you familiar with The Elm Architecture in the context of things like:
-->

Sua aplicação web precisará lidar com a entrada do usuário. Esta seção irá familiarizá-lo com a A Arquitetura Elm no contexto de coisas como:

<!--
  - Buttons
  - Text Fields
  - Check Boxes
  - Radio Buttons
  - etc.
-->

  - Botões
  - Campos de texto
  - Checkbox
  - Radio
  - etc.

<!--
We will go through a few examples that build knowledge gradually, so go in order!
-->

Iremos ver alguns exemplos para construir conhecimento gradualmente, então vá em frente!


<!--
## Follow Along
-->

## Para seguir a explicação

<!--
In the last section we used `elm repl` to get comfortable with Elm expressions. In this section, we are switching to creating Elm files of our own. You can do that in [the online editor](https://ellie-app.com/new), or if you have Elm [installed](/install.html), you can follow [these simple instructions](https://github.com/evancz/elm-architecture-tutorial#run-the-examples) to get everything working on your computer!
-->

Na última seção, usamos `elm repl` para nos familiarizarmos com expressões Elm. Nesta seção, estamos mudando para criar nossos próprios arquivos Elm. Você pode fazer isso no [editor on-line](https://ellie-app.com/new), ou se você tiver o Elm [instalado](/install.html), você pode seguir [estas instruções simples](https://github.com/evancz/elm-architecture-tutorial#run-the-examples) para que tudo funcione no seu computador!
