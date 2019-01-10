---
title: Referência de palavras-chave
description: Encontre links para informações sobre todos os F# palavras-chave.
ms.date: 05/16/2016
ms.openlocfilehash: 75adc609dc6feeda2be9aa76bbb50b47b3d738ea
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611744"
---
# <a name="keyword-reference"></a>Referência de palavras-chave

Este tópico contém links para informações sobre todos os F# palavras-chave.

## <a name="f-keyword-table"></a>F#Palavra-chave tabela

A tabela a seguir mostra todos os F# palavras-chave em ordem alfabética, junto com descrições breves e links para tópicos relevantes que contêm mais informações.

|Palavra-chave|Link|Descrição|
|-------|----|-----------|
|`abstract`|[Membros](members/index.md)<br /><br />[Classes Abstratas](abstract-classes.md)|Indica um método que seja o tipo no qual ele é declarado ou que é virtual e tem uma implementação padrão não tem nenhuma implementação.|
|`and`|[`let` Associações](functions/let-bindings.md)<br /><br />[Membros](members/index.md)<br /><br />[Restrições](generics/constraints.md)|Usado em mutuamente associações recursivas, em declarações de propriedade e com várias restrições em parâmetros genéricos.|
|`as`|[Classes](classes.md)<br /><br />[Correspondência Padrão](Pattern-Matching.md)|Usado para dar um nome de objeto de objeto de classe atual. Também é usado para fornecer um nome a um padrão de todo dentro de uma correspondência de padrões.|
|`assert`|[Asserções](assertions.md)|Usado para verificar o código durante a depuração.|
|`base`|[Classes](classes.md)<br /><br />[Herança](inheritance.md)|Usado como o nome do objeto da classe base.|
|`begin`|[Sintaxe Detalhada](verbose-syntax.md)|Na sintaxe detalhada, indica o início de um bloco de código.|
|`class`|[Classes](classes.md)|Na sintaxe detalhada, indica o início de uma definição de classe.|
|`default`|[Membros](members/index.md)|Indica uma implementação de um método abstrato; usado junto com uma declaração de método abstrato para criar um método virtual.|
|`delegate`|[Delegados](delegates.md)|Usada para declarar um delegado.|
|`do`|[Associações do](functions/do-bindings.md)<br /><br />[Loops: `for...to` Expressão](loops-for-to-expression.md)<br /><br />[Loops: `for...in` Expressão](loops-for-in-expression.md)<br /><br />[Loops: `while...do` Expressão](loops-while-do-expression.md)|Usado em construções em loop ou executar o código obrigatório.|
|`done`|[Sintaxe Detalhada](verbose-syntax.md)|Na sintaxe detalhada, indica o final de um bloco de código em uma expressão de loop.|
|`downcast`|[Conversões Cast e conversões](casting-and-conversions.md)|Usado para converter em um tipo que seja inferior na cadeia de herança.|
|`downto`|[Loops: `for...to` Expressão](loops-for-to-expression.md)|Em um `for` expressão, usada quando a contagem em ordem inversa.|
|`elif`|[Expressões condicionais: `if...then...else`](conditional-expressions-if-then-else.md)|Usado na ramificação condicional. Uma forma abreviada de `else if`.|
|`else`|[Expressões condicionais: `if...then...else`](conditional-expressions-if-then-else.md)|Usado na ramificação condicional.|
|`end`|[Estruturas](structures.md)<br /><br />[Uniões Discriminadas](discriminated-unions.md)<br /><br />[Registros](records.md)<br /><br />[Extensões de Tipo](type-extensions.md)<br /><br />[Sintaxe Detalhada](verbose-syntax.md)|Em definições de tipo e extensões de tipo, indica o final de uma seção de definições de membro.<br /><br />Na sintaxe detalhada, usado para especificar o final de um bloco de código que começa com o `begin` palavra-chave.|
|`exception`|[Tratamento de Exceção](exception-handling/index.md)<br /><br />[Tipos de Exceção](exception-handling/exception-types.md)|Usada para declarar um tipo de exceção.|
|`extern`|[Funções Externas](functions/external-functions.md)|Indica que um elemento declarado do programa é definido em outro assembly ou binário.|
|`false`|[Tipos Primitivos](primitive-types.md)|Usado como um literal booliano.|
|`finally`|[Exceções: O `try...finally` expressão](exception-handling/the-try-finally-expression.md)|Usado junto com `try` para introduzir um bloco de código que é executado independentemente se ocorrer uma exceção.|
|`fixed`|[corrigido](fixed.md)|Usado para "fixar" um ponteiro na pilha para impedir que ele seja coletado como lixo.|
|`for`|[Loops: `for...to` Expressão](loops-for-to-expression.md)<br /><br />[Loops: Expressão for...in](loops-for-in-expression.md)|Usado em construções de loop.|
|`fun`|[Expressões lambda: A Palavra-chave `fun` ](functions/lambda-expressions-the-fun-keyword.md)|Usado em expressões lambda, funções anônimas também conhecido como.|
|`function`|[Expressões Match](match-expressions.md)<br /><br />[Expressões lambda: A palavra-chave fun](functions/lambda-expressions-the-fun-keyword.md)|Usado como uma alternativa mais curta para o `fun` palavra-chave e um `match` expressão em uma expressão lambda que tenha correspondência de padrão em um único argumento.|
|`global`|[Namespaces](namespaces.md)|Usado para referenciar o namespace do .NET de nível superior.|
|`if`|[Expressões condicionais: `if...then...else`](conditional-expressions-if-then-else.md)|Usado em construções de ramificação condicionais.|
|`in`|[Loops: Expressão for...in](loops-for-in-expression.md)<br /><br />[Sintaxe Detalhada](verbose-syntax.md)|Usado para expressões de sequência e, na sintaxe detalhada, para separar as expressões de associações.|
|`inherit`|[Herança](inheritance.md)|Usado para especificar uma classe base ou interface base.|
|`inline`|[Funções](functions/index.md)<br /><br />[Funções Embutidas](functions/inline-functions.md)|Usado para indicar uma função que deve ser integrada diretamente ao código do chamador.|
|`interface`|[Interfaces](interfaces.md)|Usado para declarar e implementar interfaces.|
|`internal`|[Controle de Acesso](access-control.md)|Usado para especificar que um membro é visível dentro de um assembly, mas não para fora dele.|
|`lazy`|[Computações Lentas](lazy-computations.md)|Usado para especificar um cálculo que será executada somente quando um resultado é necessária.|
|`let`|[`let` Associações](functions/let-bindings.md)|Usado para associar ou associar um nome para a função ou valor.|
|`let!`|[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)<br /><br />[Expressões de Computação](computation-expressions.md)|Usado em fluxos de trabalho assíncronos para associar um nome para o resultado de uma computação assíncrona, ou, em outras expressões de cálculo, usados para associar um nome a um resultado, que é do tipo de cálculo.|
|`match`|[Expressões Match](match-expressions.md)|Usado para a ramificação comparando um valor para um padrão.|
|`match!`|[Expressões de Computação](computation-expressions.md#match)|Usado para embutir uma chamada para uma correspondência de expressão e o padrão de computação em seu resultado.|
|`member`|[Membros](members/index.md)|Usada para declarar uma propriedade ou método em um tipo de objeto.|
|`module`|[Módulos](modules.md)|Usado para associar um nome com um grupo de tipos relacionados, valores e funções, para separar logicamente-lo em outro código.|
|`mutable`|[Associações let](functions/let-bindings.md)|Usada para declarar uma variável, ou seja, um valor que pode ser alterado.|
|`namespace`|[Namespaces](namespaces.md)|Usado para associar um nome com um grupo de módulos e tipos relacionados logicamente separá-la de outro código.|
|`new`|[Construtores](members/constructors.md)<br /><br />[Restrições](generics/constraints.md)|Usado para declarar, definir ou chamar um construtor que cria ou que pode criar um objeto.<br /><br />Também usado em restrições de parâmetro genérico para indicar que um tipo deve ter um construtor determinados.|
|`not`|[Referência de Símbolos e Operadores](symbol-and-operator-reference/index.md)<br /><br />[Restrições](generics/constraints.md)|Não, na verdade, uma palavra-chave. No entanto, `not struct` combinação é usado como uma restrição de parâmetro genérico.|
|`null`|[Valores Nulos](values/null-values.md)<br /><br />[Restrições](generics/constraints.md)|Indica a ausência de um objeto.<br /><br />Também é usado em restrições de parâmetro genérico.|
|`of`|[Uniões Discriminadas](discriminated-unions.md)<br /><br />[Delegados](delegates.md)<br /><br />[Tipos de Exceção](exception-handling/exception-types.md)|Usado em uniões discriminadas para indicar o tipo das categorias de valores e nas declarações de delegado e a exceção.|
|`open`|[Declarações de importação: A Palavra-chave `open` ](import-declarations-the-open-keyword.md)|Usado para disponibilizar o conteúdo de um namespace ou módulo sem qualificação.|
|`or`|[Referência de Símbolos e Operadores](symbol-and-operator-reference/index.md)<br /><br />[Restrições](generics/constraints.md)|Usado com condições Boolianas como um valor booliano `or` operador. Equivalente a '||`.<br /><br />Também é usado em restrições de membro.|
|`override`|[Membros](members/index.md)|Usado para implementar uma versão de um método abstrato ou virtual que é diferente da versão de base.|
|`private`|[Controle de Acesso](access-control.md)|Restringe o acesso a um membro para o código no mesmo tipo ou módulo.|
|`public`|[Controle de Acesso](access-control.md)|Permite o acesso a um membro de fora do tipo.|
|`rec`|[Funções](functions/index.md)|Usado para indicar que uma função é recursiva.|
|`return`|[Fluxos de Trabalho Assíncronos](Asynchronous-Workflows.md)<br /><br />[Expressões de Computação](computation-expressions.md)|Usado para indicar um valor a ser fornecido como o resultado de uma expressão de computação.|
|`return!`|[Expressões de Computação](computation-expressions.md)<br /><br />[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)|Usado para indicar uma expressão de computação que, quando avaliada, fornece o resultado da expressão contentora de computação.|
|`select`|[Expressões de Consulta](query-expressions.md)|Usado em expressões de consulta para especificar quais campos ou colunas para extrair. Observe que se trata de uma palavra-chave contextual, que significa que não é, na verdade, uma palavra reservada e atua apenas como uma palavra-chave no contexto apropriado.|
|`static`|[Membros](members/index.md)|Usado para indicar um método ou propriedade que pode ser chamada sem uma instância de um tipo ou um membro de valor que é compartilhado entre todas as instâncias de um tipo.|
|`struct`|[Estruturas](structures.md)<br /><br />[Restrições](generics/constraints.md)|Usada para declarar um tipo de estrutura.<br /><br />Também é usado em restrições de parâmetro genérico.<br /><br />Usado para compatibilidade OCaml nas definições de módulo.|
|`then`|[Expressões condicionais: `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Construtores](members/constructors.md)|Usada em expressões condicionais.<br /><br />Também é usado para executar os efeitos colaterais após a construção de objeto.|
|`to`|[Loops: `for...to` Expressão](loops-for-to-expression.md)|Usado em `for` loops para indicar um intervalo.|
|`true`|[Tipos Primitivos](primitive-types.md)|Usado como um literal booliano.|
|`try`|[Exceções: A instrução try... with expressão](exception-handling/the-try-with-expression.md)<br /><br />[Exceções: Try... expressão finally](exception-handling/the-try-finally-expression.md)|Usado para introduzir um bloco de código que pode gerar uma exceção. Usado junto com `with` ou `finally`.|
|`type`|[Tipos F#](fsharp-types.md)<br /><br />[Classes](classes.md)<br /><br />[Registros](records.md)<br /><br />[Estruturas](structures.md)<br /><br />[Enumerações](enumerations.md)<br /><br />[Uniões Discriminadas](discriminated-unions.md)<br /><br />[Abreviações de Tipo](type-abbreviations.md)<br /><br />[Unidades de Medida](units-of-measure.md)|Usado para declarar uma classe, registro, estrutura, união discriminada, tipo de enumeração, unidade de medida ou abreviação de tipo.|
|`upcast`|[Conversões Cast e conversões](casting-and-conversions.md)|Usada para converter para um tipo que é superior na cadeia de herança.|
|`use`|[Gerenciamento de recursos: A Palavra-chave `use` ](resource-management-the-use-keyword.md)|Usado em vez de `let` para valores que exigem `Dispose` a ser chamado para liberar recursos.|
|`use!`|[Expressões de Computação](computation-expressions.md)<br /><br />[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)|Usado em vez de `let!` em fluxos de trabalho assíncronos e outras expressões de computação para os valores que exigem `Dispose` a ser chamado para liberar recursos.|
|`val`|[Campos explícitos: A Palavra-chave `val` ](members/explicit-fields-the-val-keyword.md)<br /><br />[Assinaturas](signatures.md)<br /><br />[Membros](members/index.md)|Usado em uma assinatura para indicar um valor ou em um tipo para declarar um membro, em algumas situações.|
|`void`|[Tipos Primitivos](primitive-types.md)|Indica o .NET `void` tipo. Usado ao interoperar com outras linguagens .NET.|
|`when`|[Restrições](generics/constraints.md)|Usado para condições Boolianas (*quando protege*) em correspondências de padrões e introduzir uma cláusula de restrição para um parâmetro de tipo genérico.|
|`while`|[Loops: `while...do` Expressão](loops-while-do-expression.md)|Apresenta um constructo de loop.|
|`with`|[Expressões Match](match-expressions.md)<br /><br />[Expressões de Objeto](object-expressions.md)<br /><br />[Copiar e Atualizar Expressões de Registro](copy-and-update-record-expressions.md)<br /><br />[Extensões de Tipo](type-extensions.md)<br /><br />[Exceções: O `try...with` expressão](exception-handling/the-try-with-expression.md)|Usado junto com o `match` palavra-chave em expressões de correspondência. Também usado em expressões de objeto, expressões de cópias de registro e extensões de tipo para apresentar as definições de membro e apresentar os manipuladores de exceção.|
|`yield`|[Sequências](sequences.md)|Usado em uma expressão de sequência para produzir um valor para uma sequência.|
|`yield!`|[Expressões de Computação](computation-expressions.md)<br /><br />[Fluxos de Trabalho Assíncronos](asynchronous-workflows.md)|Usado em uma expressão de computação para acrescentar o resultado de uma expressão de determinada computação a um conjunto de resultados para a expressão de cálculo de recipiente.|

Os seguintes tokens estão reservados em F# porque eles são palavras-chave na linguagem OCaml:

* `asr`
* `land`
* `lor`
* `lsl`
* `lsr`
* `lxor`
* `mod`
* `sig`

Se você usar o `--mlcompatibility` opção de compilador, as palavras-chave acima estão disponíveis para uso como identificadores.

Os seguintes tokens são reservados como palavras-chave para expansão futura do F# idioma:

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
- [Referência de Símbolos e Operadores](symbol-and-operator-reference/index.md)
- [Opções do Compilador](compiler-options.md)