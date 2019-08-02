---
title: Referência de palavras-chave
description: Encontre links para informações sobre todas as palavras F# -chave de idioma.
ms.date: 05/16/2016
ms.openlocfilehash: 680b270a99eff7aa98652579d2fd31b4b05080ca
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733476"
---
# <a name="keyword-reference"></a>Referência de palavras-chave

Este tópico contém links para informações sobre todas F# as palavras-chave de idioma.

## <a name="f-keyword-table"></a>F#Tabela de palavras-chave

A tabela a seguir mostra F# todas as palavras-chave em ordem alfabética, juntamente com descrições breves e links para tópicos relevantes que contêm mais informações.

|Palavra-chave|Link|Descrição|
|-------|----|-----------|
|`abstract`|[Membros](./members/index.md)<br /><br />[Classes Abstratas](abstract-classes.md)|Indica um método que não tem nenhuma implementação no tipo no qual ele está declarado ou que é virtual e tem uma implementação padrão.|
|`and`|[`let`Associações](./functions/let-bindings.md)<br /><br />[Registros](records.md)<br /><br />[Membros](./members/index.md)<br /><br />[Restrições](./generics/constraints.md)|Usado em associações e registros recursivos mutuamente, em declarações de propriedade e com várias restrições em parâmetros genéricos.|
|`as`|[Classes](classes.md)<br /><br />[Correspondência Padrão](Pattern-Matching.md)|Usado para dar ao objeto da classe atual um nome de objeto. Também usado para dar um nome a um padrão inteiro dentro de uma correspondência de padrão.|
|`assert`|[Asserções](assertions.md)|Usado para verificar o código durante a depuração.|
|`base`|[Classes](classes.md)<br /><br />[Herança](inheritance.md)|Usado como o nome do objeto da classe base.|
|`begin`|[Sintaxe Detalhada](verbose-syntax.md)|Na sintaxe detalhada, indica o início de um bloco de código.|
|`class`|[Classes](classes.md)|Na sintaxe detalhada, indica o início de uma definição de classe.|
|`default`|[Membros](./members/index.md)|Indica uma implementação de um método abstrato; usado junto com uma declaração de método abstract para criar um método virtual.|
|`delegate`|[Delegados](delegates.md)|Usado para declarar um delegado.|
|`do`|[Associações do](./functions/do-bindings.md)<br /><br />[Loops `for...to`Expressão](loops-for-to-expression.md)<br /><br />[Loops `for...in`Expressão](loops-for-in-expression.md)<br /><br />[Loops `while...do`Expressão](loops-while-do-expression.md)|Usado em constructos de loop ou para executar código imperativo.|
|`done`|[Sintaxe Detalhada](verbose-syntax.md)|Na sintaxe detalhada, indica o final de um bloco de código em uma expressão de looping.|
|`downcast`|[Conversões Cast e conversões](casting-and-conversions.md)|Usado para converter para um tipo que é inferior na cadeia de herança.|
|`downto`|[Loops `for...to`Expressão](loops-for-to-expression.md)|Em uma `for` expressão, usada ao contar em ordem inversa.|
|`elif`|[Expressões condicionais: `if...then...else`](conditional-expressions-if-then-else.md)|Usado em ramificação condicional. Uma forma abreviada `else if`de.|
|`else`|[Expressões condicionais: `if...then...else`](conditional-expressions-if-then-else.md)|Usado em ramificação condicional.|
|`end`|[Estruturas](structures.md)<br /><br />[Uniões Discriminadas](discriminated-unions.md)<br /><br />[Registros](records.md)<br /><br />[Extensões de Tipo](type-extensions.md)<br /><br />[Sintaxe Detalhada](verbose-syntax.md)|Em definições de tipo e extensões de tipo, indica o fim de uma seção de definições de membro.<br /><br />Na sintaxe detalhada, usada para especificar o final de um bloco de código que começa com `begin` a palavra-chave.|
|`exception`|[Tratamento de Exceção](./exception-handling/index.md)<br /><br />[Tipos de Exceção](./exception-handling/exception-types.md)|Usado para declarar um tipo de exceção.|
|`extern`|[Funções Externas](./functions/external-functions.md)|Indica que um elemento de programa declarado está definido em outro binário ou assembly.|
|`false`|[Tipos Primitivos](primitive-types.md)|Usado como um literal booliano.|
|`finally`|[Exceções: A `try...finally` expressão](./exception-handling/the-try-finally-expression.md)|Usado junto com `try` para introduzir um bloco de código que é executado independentemente de ocorrer uma exceção.|
|`fixed`|[Fixado](fixed.md)|Usado para "fixar" um ponteiro na pilha para impedir que ele seja coletado pelo lixo.|
|`for`|[Loops `for...to`Expressão](loops-for-to-expression.md)<br /><br />[Loops: Expressão for...in](loops-for-in-expression.md)|Usado em construções de looping.|
|`fun`|[Expressões lambda: A Palavra-chave `fun` ](./functions/lambda-expressions-the-fun-keyword.md)|Usado em expressões lambda, também conhecidas como funções anônimas.|
|`function`|[Expressões Match](match-expressions.md)<br /><br />[Expressões lambda: A palavra-chave Fun](./functions/lambda-expressions-the-fun-keyword.md)|Usado como uma alternativa mais curta para a `fun` palavra-chave `match` e uma expressão em uma expressão lambda que tem correspondência de padrões em um único argumento.|
|`global`|[Namespaces](namespaces.md)|Usado para referenciar o namespace .NET de nível superior.|
|`if`|[Expressões condicionais: `if...then...else`](conditional-expressions-if-then-else.md)|Usado em constructos de ramificação condicional.|
|`in`|[Loops: Expressão for...in](loops-for-in-expression.md)<br /><br />[Sintaxe Detalhada](verbose-syntax.md)|Usado para expressões de sequência e, em sintaxe detalhada, para separar expressões de associações.|
|`inherit`|[Herança](inheritance.md)|Usado para especificar uma classe base ou interface base.|
|`inline`|[Funções](./functions/index.md)<br /><br />[Funções Embutidas](./functions/inline-functions.md)|Usado para indicar uma função que deve ser integrada diretamente ao código do chamador.|
|`interface`|[Interfaces](interfaces.md)|Usado para declarar e implementar interfaces.|
|`internal`|[Controle de Acesso](access-control.md)|Usado para especificar que um membro é visível dentro de um assembly, mas não fora dele.|
|`lazy`|[Expressões Lentas](lazy-expressions.md)|Usado para especificar uma expressão que deve ser executada somente quando um resultado é necessário.|
|`let`|[`let`Associações](./functions/let-bindings.md)|Usado para associar, ou associar, um nome a um valor ou função.|
|`let!`|[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)<br /><br />[Expressões de Computação](computation-expressions.md)|Usado em fluxos de trabalho assíncronos para associar um nome ao resultado de uma computação assíncrona ou, em outras expressões de computação, usada para associar um nome a um resultado, que é do tipo de computação.|
|`match`|[Expressões Match](match-expressions.md)|Usado para ramificar comparando um valor a um padrão.|
|`match!`|[Expressões de Computação](computation-expressions.md#match)|Usado para embutir uma chamada para uma expressão de computação e correspondência de padrão em seu resultado.|
|`member`|[Membros](./members/index.md)|Usado para declarar uma propriedade ou um método em um tipo de objeto.|
|`module`|[Módulos](modules.md)|Usado para associar um nome a um grupo de tipos, valores e funções relacionados para separá-lo logicamente de outro código.|
|`mutable`|[Associações let](./functions/let-bindings.md)|Usado para declarar uma variável, ou seja, um valor que pode ser alterado.|
|`namespace`|[Namespaces](namespaces.md)|Usado para associar um nome a um grupo de tipos e módulos relacionados, para separá-lo logicamente de outro código.|
|`new`|[Construtores](./members/constructors.md)<br /><br />[Restrições](./generics/constraints.md)|Usado para declarar, definir ou invocar um construtor que cria ou que pode criar um objeto.<br /><br />Também usado em restrições de parâmetro genérico para indicar que um tipo deve ter um determinado Construtor.|
|`not`|[Referência de Símbolos e Operadores](./symbol-and-operator-reference/index.md)<br /><br />[Restrições](./generics/constraints.md)|Na verdade, não é uma palavra-chave. No entanto, `not struct` em combinação é usada como uma restrição de parâmetro genérico.|
|`null`|[Valores Nulos](./values/null-values.md)<br /><br />[Restrições](./generics/constraints.md)|Indica a ausência de um objeto.<br /><br />Também usado em restrições de parâmetro genérico.|
|`of`|[Uniões Discriminadas](discriminated-unions.md)<br /><br />[Delegados](delegates.md)<br /><br />[Tipos de Exceção](./exception-handling/exception-types.md)|Usado em uniões discriminadas para indicar o tipo de categorias de valores e em declarações de delegado e exceção.|
|`open`|[Declarações de importação: A Palavra-chave `open` ](import-declarations-the-open-keyword.md)|Usado para tornar o conteúdo de um namespace ou módulo disponível sem qualificação.|
|`or`|[Referência de Símbolos e Operadores](./symbol-and-operator-reference/index.md)<br /><br />[Restrições](./generics/constraints.md)|Usado com condições booleanas como um operador `or` booliano. Equivalente a `||`.<br /><br />Também usado em restrições de membro.|
|`override`|[Membros](./members/index.md)|Usado para implementar uma versão de um método abstrato ou virtual que difere da versão base.|
|`private`|[Controle de Acesso](access-control.md)|Restringe o acesso a um membro do código no mesmo tipo ou módulo.|
|`public`|[Controle de Acesso](access-control.md)|Permite o acesso a um membro de fora do tipo.|
|`rec`|[Funções](./functions/index.md)|Usado para indicar que uma função é recursiva.|
|`return`|[Fluxos de Trabalho Assíncronos](Asynchronous-Workflows.md)<br /><br />[Expressões de Computação](computation-expressions.md)|Usado para indicar um valor a ser fornecido como o resultado de uma expressão de computação.|
|`return!`|[Expressões de Computação](computation-expressions.md)<br /><br />[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)|Usado para indicar uma expressão de cálculo que, quando avaliada, fornece o resultado da expressão de computação que a contém.|
|`select`|[Expressões de Consulta](query-expressions.md)|Usado em expressões de consulta para especificar quais campos ou colunas extrair. Observe que essa é uma palavra-chave contextual, o que significa que ela não é, na verdade, uma palavra reservada e atua apenas como uma palavra-chave no contexto apropriado.|
|`static`|[Membros](./members/index.md)|Usado para indicar um método ou propriedade que pode ser chamado sem uma instância de um tipo, ou um membro de valor que é compartilhado entre todas as instâncias de um tipo.|
|`struct`|[Estruturas](structures.md)<br /><br /> [Tuplas](tuples.md)<br/><br/>[Restrições](./generics/constraints.md)|Usado para declarar um tipo de estrutura.<br /><br/>Usado para especificar uma tupla de struct.<br/><br />Também usado em restrições de parâmetro genérico.<br /><br />Usado para compatibilidade de OCaml em definições de módulo.|
|`then`|[Expressões condicionais: `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Construtores](./members/constructors.md)|Usado em expressões condicionais.<br /><br />Também usado para executar efeitos colaterais após a construção do objeto.|
|`to`|[Loops `for...to`Expressão](loops-for-to-expression.md)|Usado em `for` loops para indicar um intervalo.|
|`true`|[Tipos Primitivos](primitive-types.md)|Usado como um literal booliano.|
|`try`|[Exceções: A tentativa... Expressão with](./exception-handling/the-try-with-expression.md)<br /><br />[Exceções: A tentativa... Expressão finally](./exception-handling/the-try-finally-expression.md)|Usado para introduzir um bloco de código que pode gerar uma exceção. Usado junto com `with` ou `finally`.|
|`type`|[Tipos F#](fsharp-types.md)<br /><br />[Classes](classes.md)<br /><br />[Registros](records.md)<br /><br />[Estruturas](structures.md)<br /><br />[Enumerações](enumerations.md)<br /><br />[Uniões Discriminadas](discriminated-unions.md)<br /><br />[Abreviações de Tipo](type-abbreviations.md)<br /><br />[Unidades de Medida](units-of-measure.md)|Usado para declarar uma classe, registro, estrutura, união discriminada, tipo de enumeração, unidade de medida ou abreviação de tipo.|
|`upcast`|[Conversões Cast e conversões](casting-and-conversions.md)|Usado para converter para um tipo que é superior na cadeia de herança.|
|`use`|[Gerenciamento de recursos: A Palavra-chave `use` ](resource-management-the-use-keyword.md)|Usado em vez `let` de para valores que `Dispose` precisam ser chamados para liberar recursos.|
|`use!`|[Expressões de Computação](computation-expressions.md)<br /><br />[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)|Usado em vez `let!` de fluxos de trabalho assíncronos e outras expressões de computação para `Dispose` valores que precisam ser chamados para liberar recursos.|
|`val`|[Campos explícitos: A Palavra-chave `val` ](./members/explicit-fields-the-val-keyword.md)<br /><br />[Assinaturas](signatures.md)<br /><br />[Membros](./members/index.md)|Usado em uma assinatura para indicar um valor ou em um tipo para declarar um membro, em situações limitadas.|
|`void`|[Tipos Primitivos](primitive-types.md)|Indica o tipo `void` .net. Usado ao interoperar com outras linguagens .NET.|
|`when`|[Restrições](./generics/constraints.md)|Usado para condições booleanas (*quando protetores*) em correspondências de padrões e para introduzir uma cláusula de restrição para um parâmetro de tipo genérico.|
|`while`|[Loops `while...do`Expressão](loops-while-do-expression.md)|Apresenta uma construção de looping.|
|`with`|[Expressões Match](match-expressions.md)<br /><br />[Expressões de Objeto](object-expressions.md)<br /><br />[Copiar e Atualizar Expressões de Registro](copy-and-update-record-expressions.md)<br /><br />[Extensões de Tipo](type-extensions.md)<br /><br />[Exceções: A `try...with` expressão](./exception-handling/the-try-with-expression.md)|Usado junto com a `match` palavra-chave em expressões de correspondência de padrões. Também usado em expressões de objeto, expressões de cópia de registro e extensões de tipo para introduzir definições de membro e para introduzir manipuladores de exceção.|
|`yield`|[Sequências](sequences.md)|Usado em uma expressão de sequência para produzir um valor para uma sequência.|
|`yield!`|[Expressões de Computação](computation-expressions.md)<br /><br />[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)|Usado em uma expressão de computação para acrescentar o resultado de uma determinada expressão de computação a uma coleção de resultados para a expressão de computação que a contém.|

Os seguintes tokens são reservados F# no porque são palavras-chave no idioma OCaml:

* `asr`
* `land`
* `lor`
* `lsl`
* `lsr`
* `lxor`
* `mod`
* `sig`

Se você usar a `--mlcompatibility` opção do compilador, as palavras-chave acima estarão disponíveis para uso como identificadores.

Os seguintes tokens são reservados como palavras-chave para expansão futura do F# Idioma:

* `atomic`
* `break`
* `checked`
* `component`
* `const`
* `constraint`
* `constructor`
* `continue`
* `eager`
* `event`
* `external`
* `functor`
* `include`
* `method`
* `mixin`
* `object`
* `parallel`
* `process`
* `protected`
* `pure`
* `sealed`
* `tailcall`
* `trait`
* `virtual`
* `volatile`

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Referência de Símbolos e Operadores](./symbol-and-operator-reference/index.md)
- [Opções do Compilador](compiler-options.md)
