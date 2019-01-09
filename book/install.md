<!--
> **Note:** If you do not want to install yet, you can follow along anyway. Most sections can be done in an online editor!
-->

> **Nota:** Se você não deseja instalar ainda, você pode acompanhar o guia de qualquer maneira. A maioria das seções podem ser feitas em um editor online!


<!--
# Install

  * Mac &mdash; [installer][mac]
  * Windows &mdash; [installer][win]
  * Anywhere &mdash; [direct download][gh] or [npm][]

[mac]: https://github.com/elm/compiler/releases/download/0.19.0/installer-for-mac.pkg
[win]: https://github.com/elm/compiler/releases/download/0.19.0/installer-for-windows.exe
[npm]: https://www.npmjs.com/package/elm
[gh]: https://github.com/elm/compiler/releases/tag/0.19.0

After installing through any of those routes, you will have the `elm` binary available in your terminal!

> **Troubleshooting:** The fastest way to learn *anything* is to talk with other people in the Elm community. We are friendly and happy to help! So if you get stuck during installation or encounter something weird, visit [the Elm Slack](http://elmlang.herokuapp.com/) and ask about it. In fact, if you run into something confusing at any point while learning or using Elm, come ask us about it. You can save yourself hours. Just do it!
-->

# Instalação

  * Mac &mdash; [Instalador][mac]
  * Windows &mdash; [Instalador][win]
  * Linux &mdash; [link direto][linux]

[mac]: https://github.com/elm/compiler/releases/download/0.19.0/installer-for-mac.pkg
[win]: https://github.com/elm/compiler/releases/download/0.19.0/installer-for-windows.exe
[linux]: https://gist.github.com/evancz/442b56717b528f913d1717f2342a295d
[npm]: https://www.npmjs.com/package/elm

Depois de instalar através de qualquer uma dessas opções, você terá o binário `elm` disponível em seu terminal!

> **Resolução de problemas** A maneira mais rápida de aprender *qualquer coisa*, é conversando com outras pessoas na comunidade Elm. Nós somos amigáveis e felizes em ajudar! Então, se você ficar preso durante a instalação ou encontrar algo estranho, visite o [Slack Elm](http://elmlang.herokuapp.com/) e pergunte. De fato, se você se deparar com algo confuso a qualquer momento enquanto aprende ou usa Elm, venha nos perguntar sobre isso. Você pode economizar horas. Apenas faça!


<!--
## Configure Your Editor

Using Elm is way nicer when you have a code editor to help you out. There are Elm plugins for at least the following editors:

  * [Atom](https://atom.io/packages/language-elm)
  * [Brackets](https://github.com/lepinay/elm-brackets)
  * [Emacs](https://github.com/jcollard/elm-mode)
  * [IntelliJ](https://github.com/klazuka/intellij-elm)
  * [Light Table](https://github.com/rundis/elm-light)
  * [Sublime Text](https://packagecontrol.io/packages/Elm%20Language%20Support)
  * [Vim](https://github.com/ElmCast/elm-vim)
  * [VS Code](https://github.com/sbrink/vscode-elm)

If you do not have an editor at all, [Sublime Text](https://www.sublimetext.com/) is a great one to get started with!

You may also want to try out [elm-format][] which makes your code pretty!

[elm-format]: https://github.com/avh4/elm-format
-->


## Configure Your Editor

Usar o Elm é muito melhor quando você tem um editor de código para ajudá-lo. Existem plugins Elm para os seguintes editores:

  * [Atom](https://atom.io/packages/language-elm)
  * [Brackets](https://github.com/lepinay/elm-brackets)
  * [Emacs](https://github.com/jcollard/elm-mode)
  * [IntelliJ](https://github.com/klazuka/intellij-elm)
  * [Light Table](https://github.com/rundis/elm-light)
  * [Sublime Text](https://packagecontrol.io/packages/Elm%20Language%20Support)
  * [Vim](https://github.com/ElmCast/elm-vim)
  * [VS Code](https://github.com/sbrink/vscode-elm)

Se você não tiver nenhum editor, o [Sublime Text](https://www.sublimetext.com/) é ótimo para começar!

Você também pode querer experimentar [elm-format][] que torna o seu código bonito!

[elm-format]: https://github.com/avh4/elm-format

<!--
## Terminal Tools

So we have this `elm` binary now, but what can it do exactly?
-->

## Ferramentas para terminal
Então, nós temos esse binário `elm` agora, mas o que ele pode fazer exatamente?

<!--
### `elm repl`

`elm repl` lets us interact with Elm expressions in the terminal.

```elm
$ elm repl
---- Elm 0.19.0 ----------------------------------------------------------------
Read <https://elm-lang.org/0.19.0/repl> to learn more: exit, help, imports, etc.
--------------------------------------------------------------------------------
> 1 / 2
0.5 : Float
> List.length [1,2,3,4]
4 : Int
> String.reverse "stressed"
"desserts" : String
> :exit
$
```

We will be using `elm repl` in the upcoming &ldquo;Core Language&rdquo; section, and you can read more about how it works [here](https://elm-lang.org/0.19.0/repl).

> **Note:** `elm repl` works by compiling code to JavaScript, so make sure you have [Node.js](http://nodejs.org/) installed. We use that to evaluate code.
-->

### `elm repl`
`elm repl` nos permite interagir com expressões Elm no terminal.

```elm
$ elm repl
---- Elm 0.19.0 ----------------------------------------------------------------
Read <https://elm-lang.org/0.19.0/repl> to learn more: exit, help, imports, etc.
--------------------------------------------------------------------------------
> 1 / 2
0.5 : Float
> List.length [1,2,3,4]
4 : Int
> String.reverse "stressed"
"desserts" : String
> :exit
$
```

**Nota:** `elm repl` funciona compilando código para JavaScript, então tenha certeza que você tem o [Node.js](http://nodejs.org/) instalado. Usamos isso para avaliar o código.


<!--
### `elm reactor`

`elm reactor` helps you build Elm projects without messing with the terminal too much. You just run it at the root of your project, like this:

```bash
git clone https://github.com/evancz/elm-architecture-tutorial.git
cd elm-architecture-tutorial
elm reactor
```

This starts a server at [`http://localhost:8000`](http://localhost:8000). You can navigate to any Elm file and see what it looks like. Try to check out `examples/01-button.elm`.
-->

### `elm reactor`
`elm reactor` ajuda você a construir projetos de Elm sem mexer muito no terminal. Você apenas executa o comando na raiz do seu projeto, assim:

```bash
git clone https://github.com/evancz/elm-architecture-tutorial.git
cd elm-architecture-tutorial
elm reactor
```

Com este comando, irá iniciar um servidor em [`http://localhost:8000`](http://localhost:8000). Você pode navegar em qualquer arquivo Elm e ver o que parece. Tente acessar `examples/01-button.elm` no navegador.

<!--
## `elm make`

`elm make` builds Elm projects. It can compile Elm code to HTML or JavaScript. It is the most general way to compile Elm code, so if your project becomes too advanced for `elm reactor`, you will want to start using `elm make` directly.

Say you want to compile `Main.elm` to an HTML file named `main.html`. You would run this command:

```bash
elm make Main.elm --output=main.html
```
-->

### `elm make`
`elm make` constrói projetos Elm. Pode compilar o código Elm para HTML ou JavaScript. É a maneira mais comum de compilar o código Elm, então se o seu projeto se tornar muito avançado para o `elm reactor`, você pode optar por usar o` elm make` diretamente.

Digamos que você queira compilar `Main.elm` para um arquivo HTML chamado` main.html`. Você executaria este comando:

```bash
elm make Main.elm --output=main.html
```

<!--
### `elm install`

Elm packages all live at [`package.elm-lang.org`](https://package.elm-lang.org/).

Say you look around and decide you need [`elm/http`][http] and [`elm/json`][json] to make some HTTP requests. You can get them set up in your project with the following commands:

```bash
elm install elm/http
elm install elm/json
```

This will add the dependencies into your `elm.json` file, described in more detail [here](https://github.com/elm/compiler/blob/master/docs/elm.json/application.md).

[http]: https://package.elm-lang.org/packages/elm/http/latest
[json]: https://package.elm-lang.org/packages/elm/json/latest
-->

### `elm install`

Todos os pacotes Elm podem ser encontrados em [`package.elm-lang.org`](https://package.elm-lang.org/).

Vamos supor que, em um belo dia seu projeto precise fazer requisições HTTP [`elm/http`][http] e manipular [`elm/json`][json]. Você pode configurá-los em seu projeto com os seguintes comandos:

```bash
elm install elm/http
elm install elm/json
```

Isto irá adicionar as dependências em seu arquivo `elm.json`, descrito em mais detalhes [aqui](https://github.com/elm/compiler/blob/master/docs/elm.json/application.md).

[http]: https://package.elm-lang.org/packages/elm/http/latest
[json]: https://package.elm-lang.org/packages/elm/json/latest

<!--
## Resumo
The `elm` binary can do a bunch of stuff. Do not worry about remembering it all. You can always just run `elm --help` or `elm repl --help` to get a bunch of information about any of these commands.

Next we are going to learn the basics of Elm!
-->

## まとめ
O binário `elm` pode fazer um monte de coisas. Não se preocupe em lembrar de tudo. Você pode simplesmente executar o comando `elm --help` ou` elm repl --help` para obter várias informações sobre qualquer um desses comandos.

Em seguida, vamos aprender o básico de Elm!
