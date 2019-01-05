# Tradução para Português do guide.elm-lang.org

[Versão Original](https://github.com/evancz/guide.elm-lang.org/)

Projeto de tradução para língua portuguesa do guia de introdução a Elm guide.elm-lang.org 

Às vezes, mesclamos as alterações do projeto original.

## Progresso

Atualmente existem muitos textos originais, então incluindo `<meta name =" robots "content =" noindex ">` em todas as páginas,
Isso impede que seja considerado como conteúdo de cópia dos mecanismos de pesquisa.

## Contribuir para a tradução

O que? Contribuir?!
É super útil!

### Contribuindo como revisor

Também estamos procurando pessoas que possam revisar o conteúdo traduzido por outras pessoas!
O trabalho de tradução e participação como revisores são muito apreciados!

### Como traduzir

`./book` Comente a sentença original em inglês e, na linha seguinte do arquivo, preencha o trecho em português.
[Exemplo] (https://github.com/elm-jp/guide/pull/1)

```bash
$ npx pretranslate ./book/your_file_to_translate
```

Comente o arquivo de destino automaticamente para cada parágrafo, executando-o automaticamente e, adicionalmente, acrescente um padrão bilingue do termo que aparece na sentença de acordo com a tabela bilíngüe `./Book/about_translation.md`.

A própria tabela bilíngüe precisa ser atualizada manualmente. Por favor, adicione-o à tabela de tradução sempre que traduzir palavras importantes.

### Depois de decidir traduzir

Para evitar várias pessoas trabalhando no mesmo trecho do guia, primeiro procure o problema correspondente e comente "Vou traduzir este arquivo" ou se você tiver a permissão, por favor, atribua a o issue a si mesmo.
É recomendado porque outras pessoas notam que o projeto está andando: "Ah, isso está progredindo!".

Além disso, embora seja opcional, você pode criar um pull request e ir atualizando com novos commits conforme progride. Uma forma de começar é com um commit vazio:

```bash
$ git checkout -b ${your_branch_name}
$ git commit --allow-empty -m 'Empty commit'
$ git push origin ${your_branch_name}
```

Você pode começar o nome do PR com `[WIP]` (work in progress) para sinalizar que ainda não está completo, por exemplo:  `[WIP] interop / flags.md`.

## Rodando localmente

Para instalar (`yarn` também funciona):

```bash
$ npm i
$ npm run install
```

Para iniciar o servidor de desenvolvimento:

```bash
$ npm start
...
...
Starting server ...
Serving book on http://localhost:4000
```

Acesse em `http://localhost:4000`

## Implantar no ambiente de produção

```bash
$ git checkout master
$ npm run build
$ git add docs && git commit -m 'Update docs' && git push origin master
```
