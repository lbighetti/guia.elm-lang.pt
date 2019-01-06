
<!--
# Core Language
-->

# Fundamentos da Linguagem

<!--
This section will walk you through Elm's simple core language.
-->

Essa sessão irá te demonstrar aspectos fundamentais do Elm

<!--
This works best when you follow along, so after [installing](install.md), run `elm repl` in the terminal. You should see something like this:
-->

Todo esse guia foi feito para que você consiga reproduzir cada passo, depois da [instalação](install.md), execute `elm repl` no terminal. Você verá algo como:

```elm
---- Elm 0.19.0 ----------------------------------------------------------------
Read <https://elm-lang.org/0.19.0/repl> to learn more: exit, help, imports, etc.
--------------------------------------------------------------------------------
>
```

<!--
The REPL prints out the type of every result, but **we will leave the type annotations off in this tutorial** for the sake of introducing concepts gradually.
-->

O REPL escreve o tipo de cada resultado, mas **deixaremos anotações de tipo fora desse tutorial** para que seja possível introduzir os conceitos de forma gradual.


<!--
We will cover [values](#values), [functions](#functions), [lists](#lists), [tuples](#tuples), and [records](#records). These building blocks all correspond pretty closely with structures in languages like JavaScript, Python, and Java.
-->

Iremos cobrir [valores](#values), [funções](#functions), [listas](#lists), [tuplas](#tuples) e [registros](#records). Esses serão os conceitos fundamentais, e são correspondentes próximos com estrutras de linguagens como Javascript, Python e Java.

<!--
## Values
-->

## Valores


<!--
Let's get started with some strings:
-->

Vamos começar com algumas strings:

```elm
> "hello"
"hello"

> "hello" ++ "world"
"helloworld"

> "hello" ++ " world"
"hello world"
```

<!--
Elm uses the `(++)` operator to put strings together. Notice that both strings are preserved exactly as is when they are put together so when we combine `"hello"` and `"world"` the result has no spaces.
-->

Elm usa o operador `(++)` para juntar strings. Perceba que as strings são preservadas durante a execução do operador, então quando combinamos `"hello"` e `"world"` o resultado nao tem espaços.

<!--
Math looks normal too:
-->

Matemática também é como esperado:

```elm
> 2 + 3 * 4
14

> (2 + 3) * 4
20
```

<!--
Unlike JavaScript, Elm makes a distinction between integers and floating point numbers. Just like Python 3, there is both floating point division `(/)` and integer division `(//)`.
-->

Diferente do Javascript, Elm distingue entre inteiros (`int`) e números reais (`float`).  Assim como no Python 3 há uma divisão para números reais `(/)` e divisão de inteiros `(//)`.

```elm
> 9 / 2
4.5

> 9 // 2
4
```

<!--
## Functions
-->

## Funções

<!--
Let's start by writing a function `isNegative` that takes in some number and checks if it is less than zero. The result will be `True` or `False`.
-->

Vamos começar escrevendo a função `isNegative`, que recebe um número e verifica se é menor que zero. O resultado será `True` ou `False`.

```elm
> isNegative n = n < 0
<function>

> isNegative 4
False

> isNegative -7
True

> isNegative (-3 * -4)
False
```

<!--
Notice that function application looks different than in languages like JavaScript and Python and Java. Instead of wrapping all arguments in parentheses and separating them with commas, we use spaces to apply the function. So `(add(3,4))` becomes `(add 3 4)` which ends up avoiding a bunch of parens and commas as things get bigger. Ultimately, this looks much cleaner once you get used to it! The [elm/html][html] package is a good example of how this keeps things feeling light.
-->

Perceba que a aplicação da função parece diferente de outras linguagens como Javascript, Python e Java. Ao invés de adicionar parênteses entre os argumentos e separó-los por vírgulas, nós usamos espaços para executar a função. Então termos como `(add(3,4))` vira `(add 3 4)` o que acaba evitando vários parênteses e virgulas conforme o código aumenta. Em ultima instância, parece bem mais claro uma vez que se habitua com isso! O pacote [elm/html][html] é um bom exemplo de como isso ajuda a manter o código leve.

[html]: https://elm-lang.org/blog/blazing-fast-html-round-two

<!--
You can also define _anonymous functions_ like this:
-->

**Funções anônimas** podem ser definidas da seguinte maneira:

```elm
> \n -> n < 0
<function>

> (\n -> n < 0) 4
False
```

<!--
This anonymous function is the same as `isNegative`, it just is not named! Also, the parentheses in `(\n -> n < 0) 4` are important. After the arrow, Elm is just going to keep reading code as long as it can. The parentheses put bounds on this, indicating where the function body ends. This helps Elm know that `4` is an argument to the function.
-->

Essa função anonima é a mesma que `isNegative`, mas nao foi nomeada! Além disso os parênteses em `(\n -> n < 0) 4` são importantes. Depois da seta `->`, Elm vai continuar lendo o código até onde puder. O parênteses impõe um limite nisso, indicando onde o corpo da função acaba. Isso ajuda Elm a saber que `4` é um argumento para a função.

<!--
> **Note:** The backslash that starts anonymous functions is supposed to look like a lambda `λ` if you squint. This is a possibly ill-conceived wink to the intellectual history that led to languages like Elm.
-->

> **Nota:** A barra invertida no começo da função anônima tem a intenção de se parecer com um lambda `λ`. Isso é referencia para a história intelectual que levou a criação de linguagens como o Elm.

<!--
## If Expressions
-->

## Expressões condicionais `if`

<!--
When you want to have conditional behavior in Elm, you use an if-expression.
-->

No Elm quando se tem um comportamento condicional, se usa uma expressão `if`.

```elm
> if True then "hello" else "world"
"hello"

> if False then "hello" else "world"
"world"
```

<!--
The keywords `if` `then` `else` are used to separate the conditional and the two branches so we do not need any parentheses or curly braces.
-->

As palavras-chave `if`, `then` e `else` são utilizadas para separar condições e ambas ramificações, assim não precisamos de parênteses ou chaves.

<!--
Elm does not have a notion of &ldquo;truthiness&rdquo; so numbers and strings and lists cannot be used as boolean values. If we try it out, Elm will tell us that we need to work with a real boolean value.
-->

Elm nao carrega a noção de "truthiness", portanto números, strings e listas não podem ser usados como valores booleanos. Se tentarmos, Elm vai nos mostrar que precisamos trabalhar com um valore booleano de verdade.

<!--
Now let's make a function that tells us if a number is over 9000.
-->

Vamos criar uma função que nos mostra se um número é de mais de 8000.

```elm
> over8000 powerLevel = \
|   if powerLevel > 8000 then "It's over 8000!!!" else "meh"
<function>

> over8000 42
"meh"

> over8000 100000
"It's over 8000!!!"
```

<!--
Using a backslash in the REPL lets us split things on to multiple lines. We use this in the definition of `over9000` above. Furthermore, it is best practice to always bring the body of a function down a line. It makes things a lot more uniform and easy to read, so you want to do this with all the functions and values you define in normal code.
-->

Usando a barra invertida no REPL nos permite dividir nosso código em diversas linhas. Nós usamos isso na definição de `over8000` acima. Além disso é sempre uma boa prática deixar o corpo da função uma linha abaixo. Isso faz as coisas muito mais uniformes e fáceis de ler, então é preferível que isso seja usado em valores e funções no seu código normalmente.

<!--
> **Note:** Make sure that you add a whitespace before the second line of the function. Elm has a "syntactically significant whitespace" meaning that indentation is a part of its syntax.
-->

> **Nota:** Certifique-se que há um espaço antes da segunda linha da função. Elm possuí "espaço síntaticamente significante" isso significa que a identação é parte da sintáxe.

<!--
## Lists
-->

## Listas

<!--
Lists are one of the most common data structures in Elm. They hold a sequence of related things, similar to arrays in JavaScript.
-->

Listas são uma das estruturas de dados mais comuns no Elm. É uma sequência de elementos relacionados, similar a arrays no Javascript.

<!--
Lists can hold many values. Those values must all have the same type. Here are a few examples that use functions from the [`List`][list] module:
-->

Uma lista pode conter vários valores. Esses valores devem ser todos do mesmo tipo. Esses são alguns exemplos usando funções do módulo [`List`][list]:


[list]: https://package.elm-lang.org/packages/elm/core/latest/List

```elm
> names = [ "Alice", "Bob", "Chuck" ]
["Alice","Bob","Chuck"]

> List.isEmpty names
False

> List.length names
3

> List.reverse names
["Chuck","Bob","Alice"]

> numbers = [1,4,3,2]
[1,4,3,2]

> List.sort numbers
[1,2,3,4]

> double n = n * 2
<function>

> List.map double numbers
[2,8,6,4]
```

<!--
Again, all elements of the list must have the same type.
-->

Reforçando, todos os elementos da lista devem ter o mesmo tipo.


<!--
## Tuples
-->

## Tuplas

<!--
Tuples are another useful data structure. A tuple can hold a fixed number of values, and each value can have any type. A common use is if you need to return more than one value from a function. The following function gets a name and gives a message for the user:
-->

Tuples são outra estrutura de dados muito úteis. Uma tupla pode ter um número fixo de valores, e cada valor pode ter qualquer tipo. Um uso comum é quando se precisa retornar mais de um valor em uma função. A função abaixo recebe um nome e devolve uma mensagem para o usuário:

```elm
> import String

> goodName name = \
|   if String.length name <= 20 then \
|     (True, "name accepted!") \
|   else \
|     (False, "name was too long; please limit it to 20 characters")

> goodName "Tom"
(True, "name accepted!")
```

<!--
This can be quite handy, but when things start becoming more complicated, it is often best to use records instead of tuples.
-->

Tuplas podem ser bem úteis, mas quando a complexidade aumentar, geralmente é melhor usar um registro (`record`).


<!--
## Records
-->

## Registros

<!--
A record is a fixed set of key-value pairs, similar to objects in JavaScript or Python. You will find that they are extremely common and useful in Elm! Let's see some basic examples.
-->

Um registro é um conjunto fixo de pares chave-valor, similar a objetos em Javascript ou Python. Você vai perceber que são extremamente comuns e úteis em Elm. Vamos ver alguns exemplos básicos.

```elm
> point = { x = 3, y = 4 }
{ x = 3, y = 4 }

> point.x
3

> bill = { name = "Gates", age = 62 }
{ age = 62, name = "Gates" }

> bill.name
"Gates"
```

<!--
So we can create records using curly braces and access fields using a dot. Elm also has a version of record access that works like a function. By starting the variable with a dot, you are saying *please access the field with the following name*. This means that `.name` is a function that gets the `name` field of the record.
-->

Podemos criar registro usando chaves e acessar campos usando um ponto. Elm também tem uma versão de acesso de registros que funciona como uma função. Ao começar a variável com um ponto, você está dizendo *por favor acesse o campo com este nome*. Isso significa que `.name` é uma função que recebe o campo `nome` do registro.


```elm
> .name bill
"Gates"

> List.map .name [bill,bill,bill]
["Gates","Gates","Gates"]
```

<!--
When it comes to making functions with records, you can do some pattern matching to make things a bit lighter.
-->

Quando estiver fazendo funções com registros, é possível usar pattern matching para tornar as coisas mais leves. 

```elm
> under70 {age} = age < 70
<function>

> under70 bill
True

> under70 { species = "Triceratops", age = 68000000 }
False
```

<!--
So we can pass any record in as long as it has an `age` field that holds a number.
-->

Podemos passar qualquer registro enquanto existir um campo com nome `age` cujo valor é um número.

<!--
It is often useful to update the values in a record.
-->

Muitas vezes é útil atualizar os valores em um registro.

```elm
> { bill | name = "Nye" }
{ age = 62, name = "Nye" }

> { bill | age = 22 }
{ age = 22, name = "Gates" }
```

<!--
It is important to notice that we do not make *destructive* updates. When we update some fields of `bill` we actually create a new record rather than overwriting the existing one. Elm makes this efficient by sharing as much content as possible. If you update one of ten fields, the new record will share the nine unchanged values.
-->

É importnate notar que não fazemos atualização **destrutiva**. Quando atualizamos alguns campos de `bill` um novo registro é
criado ao invés de sobreescrever o já existente. Elm torna isso eficiênte ao compartilhar o máximo de conteúdo possível. Se você atualizar um campo em um registro de dez campos, o novo registro vai compartilhar nove valores não alterados.

<!--
> ### Records vs Objects
>
> Records in Elm are *similar* to objects in JavaScript, but there are some important differences. With records:
>
> - You cannot ask for a field that does not exist.
> - No field will ever be `undefined` or `null`.
> - You cannot create recursive records with a `this` or `self` keyword.
>
> Elm encourages a strict separation of data and logic, and the ability to say `this` is primarily used to break this separation. This is a systemic problem in Object Oriented languages that Elm is purposely avoiding.
>
> Records also support [structural typing][st] which means records in Elm can be used in any situation as long as the necessary fields exist. This gives us flexibility without compromising reliability.

[st]: https://en.wikipedia.org/wiki/Structural_type_system "Structural Types"
-->

> ### Registros vs Objetos
>
> Registros no Elm são *similares* a objetos em Javascript, mas existem diferenças importantes. Com registros:
>
> - Não é possível pedir por um campo que não existe.
> - Nenhum campo será `undefined` ou `null`.
> - Não é possível criar registros recursivos com as palavras-chave `this` ou `self`.
>
> Elm encoraja a separação estrita entre dados e lógica, e a habilidade de usar `this` é primordialmente usada para quebrar essa separação. Isso é um problema sistêmico em linguagens orientadas a objetos que o Elm está evitando propositalmente.
>
> Esse registro também suporta [tipagem estrutural][st] que significa que registro no Elm podem ser usados em qualquer situação enquanto os campos necessários existem. Isso nos dá flexibilidade sem comprometer a confiança.


[st]: https://en.wikipedia.org/wiki/Structural_type_system "Structural Types"
