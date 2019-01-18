<!--
# Types
-->

# Tipos

<!--
One of Elm's major benefits is that **users do not see runtime errors in practice**. This is possible because the Elm compiler can analyze your source code very quickly to see how values flow through your program. If a value can ever be used in an invalid way, the compiler tells you about it with a friendly error message. This is called _type inference_. The compiler figures out what _type_ of values flow in and out of all your functions.
-->

Um dos maiores benefícios do Elm é o fato de **os usuários, na prática, não verem erros em tempo de execução**. Isso é possível pois o compilador Elm pode analizar seu código muito rapidamente para verificar como os valores transitam pelo seu programa. Se existe a possibilidade de um valor ser usado de uma forma inválida, o compilador te avisa sobre isso com uma mensagem de erro amigável. Isso é chamado _inferência de tipos_. O compilador deduz qual _tipo_ de valores flui para dentro e para fora de todas as suas funções.

<!--
## An Example of Type Inference
-->

## Um exemplo de Inferência de Tipo

<!--
The following code defines a `toFullName` function which extracts a person’s full name as a string:
-->

O código abaixo define uma função `toFullName` que extrai, como uma string, o nome completo de uma pessoa:

```elm
toFullName person =
  person.firstName ++ " " ++ person.lastName

fullName =
  toFullName { fistName = "Hermann", lastName = "Hesse" }
```

<!--
Like in JavaScript or Python, we just write the code with no extra clutter. Do you see the bug though?
-->

Como em JavaScript ou Python, nós simplesmente escrevemos o código sem nenhuma complicação extra. Mas você consegue perceber o bug?

<!--
In JavaScript, the equivalent code spits out `"undefined Hesse"`. Not even an error! Hopefully one of your users will tell you about it when they see it in the wild. In contrast, the Elm compiler just looks at the source code and tells you:
-->

Em JavaScript, o código equivalente retorna `"undefined Hesse"`. Nem mesmo um erro! Tenhamos esperança de que um dos seus usuários irá lhe falar sobre quando vir isso em produção. Em contraste, o compilador Elm simplesmente olha pro código fonte e te avisa:

```
-- TYPE MISMATCH ---------------------------------------------------------------

The argument to function `toFullName` is causing a mismatch.
# O argumento da função `toFullName` está causando um conflito

6│   toFullName { fistName = "Hermann", lastName = "Hesse" }
                ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Function `toFullName` is expecting the argument to be:
# a função `toFullName` espera que o argumento seja:

    { …, firstName : … }

But it is:
# Mas ele é:

    { …, fistName : … }

Hint: I compared the record fields and found some potential typos.
# Dica: Eu comparei os campos do registro e encontrei potenciais erros de digitação.

    firstName <-> fistName
```

<!--
It sees that `toFullName` is getting the wrong _type_ of argument. Like the hint in the error message says, someone accidentally wrote `fist` instead of `first`.
-->

Ele vê que `toFullName` está recebendo o _tipo_ errado de argumento. Como a dica na mensagem de erro diz, alguém acidentalmente escreveu `fist` ao invés de `first`.

<!--
It is great to have an assistant for simple mistakes like this, but it is even more valuable when you have hundreds of files and a bunch of collaborators making changes. No matter how big and complex things get, the Elm compiler checks that _everything_ fits together properly just based on the source code.
-->

É ótimo ter um assistente para erros simples como esse, mas ele é ainda mais valioso quando você tem centenas de arquivos e diversos colaboradores fazendo mudanças. Não importa o quão grandes e complexas as coisas fiquem, o compilador Elm garante que _tudo_ se encaixe adequadamente baseando-se apenas no código fonte.

<!--
The better you understand types, the more the compiler feels like a friendly assistant. So let's start learning more!
-->

Quanto mais você entende de tipos, mais o compilador soa como um assitente amigável. Então vamos começar a aprender mais!
