---
title: Referência de palavras-chave (F#)
description: 'Encontre links para informações sobre todas as palavras-chave F # idioma.'
ms.date: 05/16/2016
ms.openlocfilehash: 7d8a2bf667f5303cc19e8d4279e433efca25c294
ms.sourcegitcommit: c03eef711abe961a85db2b4d0715257d1524aef6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33840883"
---
# <a name="keyword-reference"></a>Referência de palavras-chave

Este tópico contém links para informações sobre todos os F # palavras-chave.

## <a name="f-keyword-table"></a>Tabela de palavra-chave F #

A tabela a seguir mostra todos os F # palavras-chave em ordem alfabética, juntamente com descrições breves e links para tópicos relevantes que contêm mais informações.

|Palavra-chave|Link|Descrição|
|-------|----|-----------|
|`abstract`|[Membros](members/index.md)<br /><br />[Classes Abstratas](abstract-classes.md)|Indica um método que não tem nenhuma implementação no tipo no qual ela é declarada ou que é virtual e tem uma implementação padrão.|
|`and`|[`let` Associações](functions/let-bindings.md)<br /><br />[Membros](members/index.md)<br /><br />[Restrições](generics/constraints.md)|Usado em mutuamente associações recursivas, em declarações de propriedade e com várias restrições em parâmetros genéricos.|
|`as`|[Classes](classes.md)<br /><br />[Correspondência Padrão](Pattern-Matching.md)|Usado para fornecer um nome de objeto do objeto da classe atual. Também é usado para dar um nome a um padrão todo dentro de uma correspondência de padrão.|
|`assert`|[Asserções](assertions.md)|Usado para verificar o código durante a depuração.|
|`base`|[Classes](classes.md)<br /><br />[Herança](inheritance.md)|Usado como o nome do objeto de classe base.|
|`begin`|[Sintaxe Detalhada](verbose-syntax.md)|Na sintaxe estendida, indica o início de um bloco de código.|
|`class`|[Classes](classes.md)|Na sintaxe estendida, indica o início de uma definição de classe.|
|`default`|[Membros](members/index.md)|Indica uma implementação de um método abstrato; usado junto com uma declaração de método abstrato para criar um método virtual.|
|`delegate`|[Delegados](delegates.md)|Usado para declarar um delegado.|
|`do`|[Associações do](functions/do-bindings.md)<br /><br />[Loops: `for...to` expressão](loops-for-to-expression.md)<br /><br />[Loops: `for...in` expressão](loops-for-in-expression.md)<br /><br />[Loops: `while...do` expressão](loops-while-do-expression.md)|Usado em construções de loop ou para executar código obrigatório.|
|`done`|[Sintaxe Detalhada](verbose-syntax.md)|Na sintaxe estendida, indica o final de um bloco de código em uma expressão de loop.|
|`downcast`|[Conversões Cast e conversões](casting-and-conversions.md)|Usado para converter um tipo que seja inferior na cadeia de herança.|
|`downto`|[Loops: `for...to` expressão](loops-for-to-expression.md)|Em um `for` expressão, usada quando a contagem na ordem inversa.|
|`elif`|[Expressões condicionais: `if...then...else`](conditional-expressions-if-then-else.md)|Usado na ramificação condicional. Uma forma abreviada de `else if`.|
|`else`|[Expressões condicionais: `if...then...else`](conditional-expressions-if-then-else.md)|Usado na ramificação condicional.|
|`end`|[Estruturas](structures.md)<br /><br />[Uniões Discriminadas](discriminated-unions.md)<br /><br />[Registros](records.md)<br /><br />[Extensões de Tipo](type-extensions.md)<br /><br />[Sintaxe Detalhada](verbose-syntax.md)|Em definições de tipo e extensões de tipo, indica o final de uma seção de definições de membro.<br /><br />Na sintaxe estendida, usado para especificar o final de um bloco de código que começa com o `begin` palavra-chave.|
|`exception`|[Tratamento de Exceção](exception-handling/index.md)<br /><br />[Tipos de Exceção](exception-handling/exception-types.md)|Usado para declarar um tipo de exceção.|
|`extern`|[Funções Externas](functions/external-functions.md)|Indica que um elemento declarado do programa é definido em outro assembly ou binário.|
|`false`|[Tipos Primitivos](primitive-types.md)|Usado como um literal booliano.|
|`finally`|[Exceções: a expressão `try...finally`](exception-handling/the-try-finally-expression.md)|Usado em conjunto com `try` apresentar um bloco de código que é executado independentemente se ocorrer uma exceção.|
|`fixed`|[fixo](fixed.md)|Usado para "fixar" um ponteiro na pilha para impedir que ele está sendo coletado como lixo.|
|`for`|[Loops: `for...to` expressão](loops-for-to-expression.md)<br /><br />[Loops: Expressão for...in](loops-for-in-expression.md)|Usado em construções de loop.|
|`fun`|[Expressões lambda: A `fun` palavra-chave](functions/lambda-expressions-the-fun-keyword.md)|Usada em expressões lambda, também conhecido como anônimas funções.|
|`function`|[Expressões Match](match-expressions.md)<br /><br />[Expressões lambda: A palavra-chave fun](functions/lambda-expressions-the-fun-keyword.md)|Usado como uma alternativa mais curto para o `fun` palavra-chave e um `match` expressão em uma expressão lambda com um padrão de correspondência em um único argumento.|
|`global`|[Namespaces](namespaces.md)|Usado para referenciar o namespace .NET de nível superior.|
|`if`|[Expressões condicionais: `if...then...else`](conditional-expressions-if-then-else.md)|Usado em construções de ramificação condicionais.|
|`in`|[Loops: Expressão for...in](loops-for-in-expression.md)<br /><br />[Sintaxe Detalhada](verbose-syntax.md)|Usado para expressões de sequência e, na sintaxe estendida, para separar expressões de associações.|
|`inherit`|[Herança](inheritance.md)|Usado para especificar uma classe base ou interface base.|
|`inline`|[Funções](functions/index.md)<br /><br />[Funções Embutidas](functions/inline-functions.md)|Usado para indicar uma função que deve ser integrada diretamente no código do chamador.|
|`interface`|[Interfaces](interfaces.md)|Usado para declarar e implementar interfaces.|
|`internal`|[Controle de Acesso](access-control.md)|Usado para especificar que um membro é visível dentro de um assembly, mas não fora dele.|
|`lazy`|[Computações Lentas](lazy-computations.md)|Usado para especificar um cálculo que será executada somente quando um resultado é necessária.|
|`let`|[`let` Associações](functions/let-bindings.md)|Usado para associar ou vincular um nome para a função ou valor.|
|`let!`|[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)<br /><br />[Expressões de Computação](computation-expressions.md)|Usada em fluxos de trabalho assíncronos para associar um nome para o resultado de uma computação assíncrona, ou, em outras expressões de cálculo, usados para vincular um nome a um resultado, o que é do tipo de computação.|
|`match`|[Expressões Match](match-expressions.md)|Usado para a ramificação comparando um valor a um padrão.|
|`member`|[Membros](members/index.md)|Usado para declarar uma propriedade ou método em um tipo de objeto.|
|`module`|[Módulos](modules.md)|Usado para associar um nome de um grupo de tipos relacionados, valores e funções, para separá-lo a lógica do código.|
|`mutable`|[Associações let](functions/let-bindings.md)|Usado para declarar uma variável, ou seja, um valor que pode ser alterado.|
|`namespace`|[Namespaces](namespaces.md)|Usado para associar um nome de um grupo de módulos e tipos relacionados logicamente separá-lo de outro código.|
|`new`|[Construtores](members/constructors.md)<br /><br />[Restrições](generics/constraints.md)|Usado para declarar, definir ou chamar um construtor que cria ou que você pode criar um objeto.<br /><br />Usado também em restrições de parâmetro genérico para indicar que um tipo deve ter um construtor determinados.|
|`not`|[Referência de Símbolos e Operadores](symbol-and-operator-reference/index.md)<br /><br />[Restrições](generics/constraints.md)|Não é realmente uma palavra-chave. No entanto, `not struct` combinação é usado como uma restrição de parâmetro genérico.|
|`null`|[Valores Nulos](values/null-values.md)<br /><br />[Restrições](generics/constraints.md)|Indica a ausência de um objeto.<br /><br />Também é usado em restrições de parâmetro genérico.|
|`of`|[Uniões Discriminadas](discriminated-unions.md)<br /><br />[Delegados](delegates.md)<br /><br />[Tipos de Exceção](exception-handling/exception-types.md)|Usado em uniões discriminadas para indicar o tipo das categorias de valores, em declarações do delegado e a exceção.|
|`open`|[Declarações de Importação: a palavra-chave `open`](import-declarations-the-open-keyword.md)|Usado para disponibilizar o conteúdo de um namespace ou módulo sem qualificação.|
|`or`|[Referência de Símbolos e Operadores](symbol-and-operator-reference/index.md)<br /><br />[Restrições](generics/constraints.md)|Usado com condições Boolean como um booliano `or` operador. Equivalente a '||`.<br /><br />Também é usado em restrições de membro.|
|`override`|[Membros](members/index.md)|Usado para implementar uma versão de um método virtual ou abstrato que difere da versão base.|
|`private`|[Controle de Acesso](access-control.md)|Restringe o acesso a um membro para o código do mesmo tipo ou módulo.|
|`public`|[Controle de Acesso](access-control.md)|Permite o acesso a um membro de fora do tipo.|
|`rec`|[Funções](functions/index.md)|Usado para indicar que uma função é recursiva.|
|`return`|[Fluxos de Trabalho Assíncronos](Asynchronous-Workflows.md)<br /><br />[Expressões de Computação](computation-expressions.md)|Usado para indicar um valor para fornecer como resultado de uma expressão de computação.|
|`return!`|[Expressões de Computação](computation-expressions.md)<br /><br />[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)|Usado para indicar uma expressão de computação que, quando avaliado, fornece o resultado da expressão de computação que contém.|
|`select`|[Expressões de Consulta](query-expressions.md)|Usado em expressões de consulta para especificar quais campos ou colunas para extrair. Observe que esta é uma palavra-chave contextual, que significa que não é realmente uma palavra reservada e apenas age como uma palavra-chave no contexto apropriado.|
|`static`|[Membros](members/index.md)|Usado para indicar um método ou propriedade que pode ser chamada sem uma instância de um tipo ou um membro de valor que é compartilhado entre todas as instâncias de um tipo.|
|`struct`|[Estruturas](structures.md)<br /><br />[Restrições](generics/constraints.md)|Usado para declarar um tipo de estrutura.<br /><br />Também é usado em restrições de parâmetro genérico.<br /><br />Usado para compatibilidade OCaml nas definições de módulo.|
|`then`|[Expressões condicionais: `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Construtores](members/constructors.md)|Usada em expressões condicionais.<br /><br />Também é usada para executar efeitos colaterais após a construção de objeto.|
|`to`|[Loops: `for...to` expressão](loops-for-to-expression.md)|Usado em `for` loops para indicar um intervalo.|
|`true`|[Tipos Primitivos](primitive-types.md)|Usado como um literal booliano.|
|`try`|[Exceções: A try... com a expressão](exception-handling/the-try-with-expression.md)<br /><br />[Exceções: A try... finally expressão](exception-handling/the-try-finally-expression.md)|Usado para introduzir um bloco de código que pode gerar uma exceção. Usado em conjunto com `with` ou `finally`.|
|`type`|[Tipos F#](fsharp-types.md)<br /><br />[Classes](classes.md)<br /><br />[Registros](records.md)<br /><br />[Estruturas](structures.md)<br /><br />[Enumerações](enumerations.md)<br /><br />[Uniões Discriminadas](discriminated-unions.md)<br /><br />[Abreviações de Tipo](type-abbreviations.md)<br /><br />[Unidades de Medida](units-of-measure.md)|Usado para declarar uma classe, registro, estrutura, união discriminada, tipo de enumeração, unidade de medida ou abreviação de tipo.|
|`upcast`|[Conversões Cast e conversões](casting-and-conversions.md)|Usado para converter para um tipo que é superior na cadeia de herança.|
|`use`|[Gerenciamento de Recursos: a palavra-chave `use`](resource-management-the-use-keyword.md)|Usado em vez de `let` para valores que exigem `Dispose` a ser chamado para liberar recursos.|
|`use!`|[Expressões de Computação](computation-expressions.md)<br /><br />[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)|Usado em vez de `let!` em fluxos de trabalho assíncronos e outras expressões de computação para valores que exigem `Dispose` a ser chamado para liberar recursos.|
|`val`|[Campos Explícitos: a `val` Palavra-Chave](members/explicit-fields-the-val-keyword.md)<br /><br />[Assinaturas](signatures.md)<br /><br />[Membros](members/index.md)|Usado em uma assinatura para indicar um valor, ou em um tipo para declarar um membro, em situações limitadas.|
|`void`|[Tipos Primitivos](primitive-types.md)|Indica o .NET `void` tipo. Usado ao interagir com outras linguagens .NET.|
|`when`|[Restrições](generics/constraints.md)|Usado para condições Boolianas (*quando protege*) em correspondências padrão e apresentar uma cláusula de restrição para um parâmetro de tipo genérico.|
|`while`|[Loops: `while...do` expressão](loops-while-do-expression.md)|Apresenta uma construção de loop.|
|`with`|[Expressões Match](match-expressions.md)<br /><br />[Expressões de Objeto](object-expressions.md)<br /><br />[Copiar e Atualizar Expressões de Registro](copy-and-update-record-expressions.md)<br /><br />[Extensões de Tipo](type-extensions.md)<br /><br />[Exceções: a expressão `try...with`](exception-handling/the-try-with-expression.md)|Usada junto com o `match` palavra-chave em expressões de correspondência de padrões. Também usado em expressões de objeto, expressões de registros de cópias e extensões de tipo para apresentar as definições de membro e apresentar os manipuladores de exceção.|
|`yield`|[Sequências](sequences.md)|Usado em uma expressão de sequência para produzir um valor para uma sequência.|
|`yield!`|[Expressões de Computação](computation-expressions.md)<br /><br />[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)|Usado em uma expressão de computação para anexar o resultado de uma expressão de computação fornecido a um conjunto de resultados para a expressão de computação que contém.|

Os seguintes tokens são reservados em F #, porque eles são palavras-chave na linguagem OCaml:

* `asr`
* `land`
* `lor`
* `lsl`
* `lsr`
* `lxor`
* `mod`
* `sig`

Se você usar o `--mlcompatibility` opção de compilador, as palavras-chave acima estão disponíveis para uso como identificadores.

Os seguintes tokens são reservados como palavras-chave para expansão futura da linguagem F #:

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
[Referência da Linguagem F#](index.md)

[Referência de Símbolos e Operadores](symbol-and-operator-reference/index.md)

[Opções do Compilador](compiler-options.md)
