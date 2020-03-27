---
title: Referência de palavras-chave
description: Encontre links para informações sobre todas as palavras-chave do idioma F#.
f1_keywords:
- new_FS
- use_FS
- end_FS
- lsl_FS
- exception_FS
- asr_FS
- if_FS
- internal_FS
- default_FS
- in_FS
- lsr_FS
- open_FS
- static_FS
- assert_FS
- match_FS
- land_FS
- with_FS
- inherit_FS
- mutable_FS
- downto_FS
- false_FS
- sig_FS
- and_FS
- true_FS
- namespace_FS
- public_FS
- lxor_FS
- val_FS
- void_FS
- downcast_FS
- function_FS
- while_FS
- for_FS
- class_FS
- done_FS
- to_FS
- module_FS
- let_FS
- delegate_FS
- abstract_FS
- then_FS
- when_FS
- lazy_FS
- try_FS
- inline_FS
- do_FS
- upcast_FS
- begin_FS
- base_FS
- fun_FS
- struct_FS
- as_FS
- extern_FS
- null_FS
- lor_FS
- return_FS
- mod_FS
- private_FS
- of_FS
- or_FS
- member_FS
- type_FS
- rec_FS
- elif_FS
- override_FS
- interface_FS
- yield_FS
- else_FS
- finally_FS
- global_FS
- select_FS
- use!_FS
dev_langs:
- FSharp
ms.date: 11/04/2019
ms.openlocfilehash: 34959f471406643e85990c2c80a38a684759a7f9
ms.sourcegitcommit: b16eacb6f94a5b601882a861ad17cc5470a8d5d5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80352316"
---
# <a name="keyword-reference"></a>Referência de palavras-chave

Este tópico contém links para informações sobre todas as palavras-chave do idioma F#.

## <a name="f-keyword-table"></a>F# Tabela de palavras-chave

A tabela a seguir mostra todas as palavras-chave F# em ordem alfabética, juntamente com breves descrições e links para tópicos relevantes que contêm mais informações.

|Palavra-chave|Link|Descrição|
|-------|----|-----------|
|`abstract`|[Membros](./members/index.md)<br /><br />[Classes Abstratas](abstract-classes.md)|Indica um método que ou não tem implementação no tipo em que é declarado ou que é virtual e tem uma implementação padrão.|
|`and`|[`let`Ligações](./functions/let-bindings.md)<br /><br />[Registros](records.md)<br /><br />[Membros](./members/index.md)<br /><br />[Restrições](./generics/constraints.md)|Usado em ligações e registros mutuamente recursivos, em declarações de propriedade e com múltiplas restrições em parâmetros genéricos.|
|`as`|[Classes](classes.md)<br /><br />[Correspondência padrão](Pattern-Matching.md)|Usado para dar ao objeto de classe atual um nome de objeto. Também costumava dar um nome a um padrão inteiro dentro de um padrão de correspondência.|
|`assert`|[Asserções](assertions.md)|Usado para verificar código durante a depuração.|
|`base`|[Classes](classes.md)<br /><br />[Herança](inheritance.md)|Usado como o nome do objeto de classe base.|
|`begin`|[Sintaxe Detalhada](verbose-syntax.md)|Na sintaxe verbosa, indica o início de um bloco de código.|
|`class`|[Classes](classes.md)|Na sintaxe verbosa, indica o início de uma definição de classe.|
|`default`|[Membros](./members/index.md)|Indica a implementação de um método abstrato; usado juntamente com uma declaração de método abstrato para criar um método virtual.|
|`delegate`|[Delegados](delegates.md)|Costumava declarar um delegado.|
|`do`|[Associações do](./functions/do-bindings.md)<br /><br />[Loops: `for...to` expressão](loops-for-to-expression.md)<br /><br />[Loops: `for...in` expressão](loops-for-in-expression.md)<br /><br />[Loops: `while...do` expressão](loops-while-do-expression.md)|Usado em construções de looping ou para executar código imperativo.|
|`done`|[Sintaxe Detalhada](verbose-syntax.md)|Na sintaxe verbosa, indica o fim de um bloco de código em uma expressão de looping.|
|`downcast`|[Conversões cast e conversões](casting-and-conversions.md)|Usado para converter para um tipo que é menor na cadeia de herança.|
|`downto`|[Loops: `for...to` expressão](loops-for-to-expression.md)|Em `for` uma expressão, usado ao contar ao contrário.|
|`elif`|[Expressões condicionais:`if...then...else`](conditional-expressions-if-then-else.md)|Usado em ramificações condicionais. Uma forma `else if`curta de.|
|`else`|[Expressões condicionais:`if...then...else`](conditional-expressions-if-then-else.md)|Usado em ramificações condicionais.|
|`end`|[Estruturas](structures.md)<br /><br />[Uniões Discriminadas](discriminated-unions.md)<br /><br />[Registros](records.md)<br /><br />[Extensões de tipo](type-extensions.md)<br /><br />[Sintaxe Detalhada](verbose-syntax.md)|Em definições de tipo e extensões de tipo, indica o fim de uma seção de definições de membros.<br /><br />Na sintaxe verbosa, usada para especificar o `begin` fim de um bloco de código que começa com a palavra-chave.|
|`exception`|[Tratamento de Exceção](./exception-handling/index.md)<br /><br />[Tipos de exceção](./exception-handling/exception-types.md)|Usado para declarar um tipo de exceção.|
|`extern`|[Funções Externas](./functions/external-functions.md)|Indica que um elemento de programa declarado é definido em outro binário ou conjunto.|
|`false`|[Tipos primitivos](basic-types.md)|Usado como um literal booleano.|
|`finally`|[Exceções: a expressão `try...finally`](./exception-handling/the-try-finally-expression.md)|Usado em `try` conjunto com para introduzir um bloco de código que executa independentemente de uma exceção ocorrer.|
|`fixed`|[Fixo](fixed.md)|Usado para "fixar" um ponteiro na pilha para evitar que fosse coletado lixo.|
|`for`|[Loops: `for...to` expressão](loops-for-to-expression.md)<br /><br />[Loops: Expressão for...in](loops-for-in-expression.md)|Usado em construções de looping.|
|`fun`|[Expressões Lambda: `fun` A Palavra-Chave](./functions/lambda-expressions-the-fun-keyword.md)|Usado em expressões lambda, também conhecidas como funções anônimas.|
|`function`|[Expressões de correspondência](match-expressions.md)<br /><br />[Lambda Expressions: A palavra-chave divertida](./functions/lambda-expressions-the-fun-keyword.md)|Usado como uma alternativa `fun` mais curta `match` à palavra-chave e uma expressão em uma expressão lambda que tem correspondência de padrão em um único argumento.|
|`global`|[Namespaces](namespaces.md)|Usado para fazer referência ao namespace .NET de nível superior.|
|`if`|[Expressões condicionais:`if...then...else`](conditional-expressions-if-then-else.md)|Usado em construções de ramificação condicional.|
|`in`|[Loops: Expressão for...in](loops-for-in-expression.md)<br /><br />[Sintaxe Detalhada](verbose-syntax.md)|Usado para expressões seqüenciais e, em sintaxe verbosa, para separar expressões de amarras.|
|`inherit`|[Herança](inheritance.md)|Usado para especificar uma classe base ou interface base.|
|`inline`|[Funções](./functions/index.md)<br /><br />[Funções inline](./functions/inline-functions.md)|Usado para indicar uma função que deve ser integrada diretamente ao código do chamador.|
|`interface`|[Interfaces](interfaces.md)|Usado para declarar e implementar interfaces.|
|`internal`|[Controle de Acesso](access-control.md)|Usado para especificar que um membro é visível dentro de uma assembléia, mas não fora dele.|
|`lazy`|[Expressões Lentas](lazy-expressions.md)|Usado para especificar uma expressão que deve ser executada somente quando um resultado é necessário.|
|`let`|[`let`Ligações](./functions/let-bindings.md)|Usado para associar, ou vincular, um nome a um valor ou função.|
|`let!`|[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)<br /><br />[Expressões de computação](computation-expressions.md)|Usado em fluxos de trabalho assíncronos para vincular um nome ao resultado de uma computação assíncrona, ou, em outras expressões de computação, usado para vincular um nome a um resultado, que é do tipo de computação.|
|`match`|[Expressões de correspondência](match-expressions.md)|Usado para ramificar comparando um valor a um padrão.|
|`match!`|[Expressões de computação](computation-expressions.md#match)|Usado para inalinhar uma chamada para uma expressão de computação e correspondência padrão em seu resultado.|
|`member`|[Membros](./members/index.md)|Usado para declarar uma propriedade ou método em um tipo de objeto.|
|`module`|[Módulos](modules.md)|Usado para associar um nome a um grupo de tipos, valores e funções relacionados, para separá-lo logicamente de outro código.|
|`mutable`|[Associações let](./functions/let-bindings.md)|Usado para declarar uma variável, ou seja, um valor que pode ser alterado.|
|`namespace`|[Namespaces](namespaces.md)|Usado para associar um nome a um grupo de tipos e módulos relacionados, para separá-lo logicamente de outro código.|
|`new`|[Construtores](./members/constructors.md)<br /><br />[Restrições](./generics/constraints.md)|Usado para declarar, definir ou invocar um construtor que cria ou que pode criar um objeto.<br /><br />Também usado em restrições de parâmetros genéricos para indicar que um tipo deve ter um certo construtor.|
|`not`|[Referência de Símbolos e Operadores](./symbol-and-operator-reference/index.md)<br /><br />[Restrições](./generics/constraints.md)|Na verdade, não é uma palavra-chave. No `not struct` entanto, em combinação é usado como uma restrição de parâmetro genérico.|
|`null`|[Valores Nulos](./values/null-values.md)<br /><br />[Restrições](./generics/constraints.md)|Indica a ausência de um objeto.<br /><br />Também usado em restrições de parâmetros genéricos.|
|`of`|[Uniões Discriminadas](discriminated-unions.md)<br /><br />[Delegados](delegates.md)<br /><br />[Tipos de exceção](./exception-handling/exception-types.md)|Usado em sindicatos discriminados para indicar o tipo de categorias de valores, e em declarações de delegados e exceções.|
|`open`|[Declarações de Importação: a palavra-chave `open`](import-declarations-the-open-keyword.md)|Usado para disponibilizar o conteúdo de um namespace ou módulo sem qualificação.|
|`or`|[Referência de Símbolos e Operadores](./symbol-and-operator-reference/index.md)<br /><br />[Restrições](./generics/constraints.md)|Usado com condições booleanas `or` como operador booleano. Equivalente a `||`.<br /><br />Também usado em restrições de membros.|
|`override`|[Membros](./members/index.md)|Usado para implementar uma versão de um método abstrato ou virtual que difere da versão base.|
|`private`|[Controle de Acesso](access-control.md)|Restringe o acesso a um membro para codificar no mesmo tipo ou módulo.|
|`public`|[Controle de Acesso](access-control.md)|Permite acesso a um membro de fora do tipo.|
|`rec`|[Funções](./functions/index.md)|Usado para indicar que uma função é recursiva.|
|`return`|[Fluxos de Trabalho Assíncronos](Asynchronous-Workflows.md)<br /><br />[Expressões de computação](computation-expressions.md)|Usado para indicar um valor para fornecer como resultado de uma expressão de computação.|
|`return!`|[Expressões de computação](computation-expressions.md)<br /><br />[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)|Usado para indicar uma expressão de computação que, quando avaliada, fornece o resultado da expressão de computação contendo.|
|`select`|[Expressões de consulta](query-expressions.md)|Usado em expressões de consulta para especificar quais campos ou colunas extrair. Note que esta é uma palavra-chave contextual, o que significa que não é realmente uma palavra reservada e só age como uma palavra-chave no contexto apropriado.|
|`static`|[Membros](./members/index.md)|Usado para indicar um método ou propriedade que pode ser chamado sem uma instância de um tipo, ou um membro de valor que é compartilhado entre todas as instâncias de um tipo.|
|`struct`|[Estruturas](structures.md)<br /><br /> [Tuplas](tuples.md)<br/><br/>[Restrições](./generics/constraints.md)|Usado para declarar um tipo de estrutura.<br /><br/>Usado para especificar uma tuplo de estrutura.<br/><br />Também usado em restrições de parâmetros genéricos.<br /><br />Usado para compatibilidade OCaml em definições de módulos.|
|`then`|[Expressões condicionais:`if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Construtores](./members/constructors.md)|Usado em expressões condicional.<br /><br />Também usado para realizar efeitos colaterais após a construção do objeto.|
|`to`|[Loops: `for...to` expressão](loops-for-to-expression.md)|Usado `for` em loops para indicar um alcance.|
|`true`|[Tipos primitivos](basic-types.md)|Usado como um literal booleano.|
|`try`|[Exceções: a expressão try...with](./exception-handling/the-try-with-expression.md)<br /><br />[Exceções: a expressão try...finally](./exception-handling/the-try-finally-expression.md)|Usado para introduzir um bloco de código que poderia gerar uma exceção. Usado junto `with` `finally`com ou .|
|`type`|[Tipos F#](fsharp-types.md)<br /><br />[Classes](classes.md)<br /><br />[Registros](records.md)<br /><br />[Estruturas](structures.md)<br /><br />[Enumerações](enumerations.md)<br /><br />[Uniões Discriminadas](discriminated-unions.md)<br /><br />[Abreviações de tipo](type-abbreviations.md)<br /><br />[Unidades de Medida](units-of-measure.md)|Usado para declarar classe, registro, estrutura, união discriminada, tipo de enumeração, unidade de medida ou abreviação tipo.|
|`upcast`|[Conversões cast e conversões](casting-and-conversions.md)|Usado para converter para um tipo que é mais alto na cadeia de herança.|
|`use`|[Gerenciamento de Recursos: a palavra-chave `use`](resource-management-the-use-keyword.md)|Usado em `let` vez de `Dispose` para valores que precisam ser chamados para recursos livres.|
|`use!`|[Expressões de computação](computation-expressions.md)<br /><br />[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)|Usado em `let!` vez de em fluxos de trabalho assíncronos e outras expressões de computação para valores que precisam `Dispose` ser chamados para recursos livres.|
|`val`|[Campos Explícitos: a `val` Palavra-Chave](./members/explicit-fields-the-val-keyword.md)<br /><br />[Assinaturas](signature-files.md)<br /><br />[Membros](./members/index.md)|Usado em uma assinatura para indicar um valor, ou em um tipo para declarar um membro, em situações limitadas.|
|`void`|[Tipos primitivos](basic-types.md)|Indica o `void` tipo .NET. Usado quando interoperando com outros idiomas .NET.|
|`when`|[Restrições](./generics/constraints.md)|Usado para condições booleanas *(quando guardas*) em correspondências de padrão e para introduzir uma cláusula de restrição para um parâmetro de tipo genérico.|
|`while`|[Loops: `while...do` expressão](loops-while-do-expression.md)|Introduz uma construção de looping.|
|`with`|[Expressões de correspondência](match-expressions.md)<br /><br />[Expressões de Objeto](object-expressions.md)<br /><br />[Copiar e atualizar expressões de registro](copy-and-update-record-expressions.md)<br /><br />[Extensões de tipo](type-extensions.md)<br /><br />[Exceções: a expressão `try...with`](./exception-handling/the-try-with-expression.md)|Usado junto `match` com a palavra-chave em expressões de correspondência de padrão. Também usado em expressões de objeto, gravar expressões de cópia e extensões de tipo para introduzir definições de membros e introduzir manipuladores de exceção.|
|`yield`|[Listas,](lists.md) [matrizes,](arrays.md) [seqüências](sequences.md)|Usado em uma lista, matriz ou expressão de seqüência para produzir um valor para uma seqüência. Normalmente pode ser omitido, pois está implícito na maioria das situações.|
|`yield!`|[Expressões de computação](computation-expressions.md)<br /><br />[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)|Usado em uma expressão de computação para anexar o resultado de uma determinada expressão computacional a uma coleção de resultados para a expressão de computação contendo.|

Os seguintes tokens são reservados em F# porque são palavras-chave no idioma OCaml:

- `asr`
- `land`
- `lor`
- `lsl`
- `lsr`
- `lxor`
- `mod`
- `sig`

Se você `--mlcompatibility` usar a opção compilador, as palavras-chave acima estão disponíveis para uso como identificadores.

Os seguintes tokens são reservados como palavras-chave para a expansão futura da língua F#:

- `atomic`
- `break`
- `checked`
- `component`
- `const`
- `constraint`
- `constructor`
- `continue`
- `eager`
- `event`
- `external`
- `functor`
- `include`
- `method`
- `mixin`
- `object`
- `parallel`
- `process`
- `protected`
- `pure`
- `sealed`
- `tailcall`
- `trait`
- `virtual`
- `volatile`

## <a name="see-also"></a>Confira também

- [Referência de idioma F#](index.md)
- [Referência de Símbolos e Operadores](./symbol-and-operator-reference/index.md)
- [Opções de compilador](compiler-options.md)
