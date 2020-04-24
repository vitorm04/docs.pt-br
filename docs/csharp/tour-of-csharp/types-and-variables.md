---
title: Tipos e variáveis do C# - um tour pela linguagem C#
description: Saiba mais sobre como definir tipos e declarar variáveis em C#
ms.date: 02/25/2020
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: dc80a7ea80790ef5af5218f5a608e5829d2970cc
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135952"
---
# <a name="types-and-variables"></a>Tipos e variáveis

Há dois tipos em C#: *tipos de referência* e *tipos de valor*. As variáveis de tipos de valor contêm diretamente seus dados enquanto variáveis de tipos de referência armazenam referências a seus dados, o último sendo conhecido como objetos. Com os tipos de referência, é possível que duas variáveis referenciem o mesmo objeto e, assim, possíveis para operações em uma variável afetem o objeto referenciado pela outra variável. Com os tipos de valor, as variáveis têm sua própria cópia dos dados, e não é possível que as operações em um afetem a outra (exceto `ref` para `out` variáveis de parâmetro e).

Os tipos de valor do C# são divididos em *tipos simples*, *tipos de enum*, *tipos struct* e *tipos de valor anulável*. Os tipos de referência do C# são divididos em *tipos de classe*, *tipos de interface*, *tipos de matriz* e *tipos delegados*.

A seguinte estrutura de tópicos fornece uma visão geral do sistema de tipos do C#.

- [Tipos de valor][ValueTypes]
  - [Tipos simples][SimpleTypes]
    - Integral com sinal: `sbyte`, `short`, `int`,`long`
    - Integral sem sinal: `byte`, `ushort`, `uint`,`ulong`
    - Caracteres Unicode: `char`
    - Ponto flutuante binário de IEEE: `float`, `double`
    - Ponto flutuante decimal de alta precisão: `decimal`
    - Booliano: `bool`
  - [Tipos de enumeração][EnumTypes]
    - Tipos definidos pelo usuário do formulário `enum E {...}`
  - [Tipos struct][StructTypes]
    - Tipos definidos pelo usuário do formulário `struct S {...}`
  - [Tipos de valor anuláveis][NullableTypes]
    - Extensões de todos os outros tipos de valor com um valor `null`
- [Tipos de referência][ReferenceTypes]
  - [Tipos de aula][ClassTypes]
    - Classe base definitiva de todos os outros tipos: `object`
    - Cadeia de caracteres Unicode: `string`
    - Tipos definidos pelo usuário do formulário `class C {...}`
  - [Tipos de interface][InterfaceTypes]
    - Tipos definidos pelo usuário do formulário `interface I {...}`
  - [Tipos de matriz][ArrayTypes]
    - Unidimensional e multidimensional, por exemplo, `int[]` e `int[,]`
  - [Tipos delegados][DelegateTypes]
    - Tipos definidos pelo usuário do formulário `delegate int D(...)`

[ValueTypes]: ../language-reference/builtin-types/value-types.md
[SimpleTypes]: ../language-reference/builtin-types/value-types.md#built-in-value-types
[EnumTypes]: ../language-reference/builtin-types/enum.md
[StructTypes]: ../language-reference/builtin-types/struct.md
[NullableTypes]: ../language-reference/builtin-types/nullable-value-types.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

Para obter mais informações sobre tipos numéricos, veja a tabela [Tipos integrais](../language-reference/builtin-types/integral-numeric-types.md) e [Tipos de ponto flutuante](../language-reference/builtin-types/floating-point-numeric-types.md).

O tipo `bool` do C# é usado para representar valores boolianos — valores que são `true` ou `false`.

O processamento de cadeia de caracteres e caracteres em C# usa codificação Unicode. O tipo `char` representa uma unidade de código UTF-16 e o tipo `string` representa uma sequência de unidades de código UTF-16.

Os programas em C# usam *declarações de tipos* para criar novos tipos. Uma declaração de tipo especifica o nome e os membros do novo tipo. Cinco das categorias do C# de tipos são tipos definidos pelo usuário: tipos de classe, tipos struct, tipos de interface, tipos enum e tipos delegados.

Um tipo `class` define uma estrutura de dados que contém membros de dados (campos) e membros de função (métodos, propriedades e outros). Os tipos de classe dão suporte à herança única e ao polimorfismo, mecanismos nos quais as classes derivadas podem estender e especializar as classes base.

Um tipo `struct` é semelhante a um tipo de classe que representa uma estrutura com membros de dados e membros da função. No entanto, ao contrário das classes, as structs são tipos de valor e normalmente não exigem alocação de heap. Tipos de struct não dão suporte à herança especificada pelo usuário e todos os tipos de struct herdam implicitamente do tipo `object`.

Um tipo `interface` define um contrato como um conjunto nomeado de membros da função pública. Um `class` ou `struct` que implementa um `interface` deve fornecer implementações de membros da função da interface. Um `interface` pode herdar de várias interfaces base e um `class` ou `struct` pode implementar várias interfaces.

Um tipo `delegate` representa referências aos métodos com uma lista de parâmetros e tipo de retorno específicos. Delegados possibilitam o tratamento de métodos como entidades que podem ser atribuídos a variáveis e passadas como parâmetros. Os delegados são análogos aos tipos de função fornecidos pelas linguagens funcionais. Eles também são semelhantes ao conceito de ponteiros de função encontrados em algumas outras linguagens. Diferentemente de ponteiros de função, os delegados são orientados a objeto e são de tipo seguro.

Os `class` `delegate` tipos `struct`, `interface`, e oferecem suporte a genéricos, no qual eles podem ser parametrizados com outros tipos.

Um tipo `enum` é um tipo distinto com constantes nomeadas. Cada tipo `enum` tem um tipo subjacente, que deve ser um dos oito tipos integrais. O conjunto de valores de um tipo `enum` é o mesmo que o conjunto de valores do tipo subjacente.

O C# dá suporte a matrizes uni e multidimensionais de qualquer tipo. Ao contrário dos tipos listados acima, os tipos de matriz não precisam ser declarados antes que possam ser usados. Em vez disso, os tipos de matriz são construídos seguindo um nome de tipo entre colchetes. Por exemplo, `int[]` é uma matriz unidimensional de `int`, `int[,]` é uma matriz bidimensional de `int`, e `int[][]` é uma matriz unidimensional da matriz unidimensional de `int`.

Os tipos de valor anulável também não precisam ser declarados antes que possam ser usados. Para cada tipo `T`de valor não anulável, há um tipo `T?`de valor anulável correspondente, que pode conter um valor adicional, `null`. Por exemplo, `int?` é um tipo que pode conter qualquer número inteiro de 32 bits ou o valor `null`.

O sistema de tipos do C# é unificado, de modo que um valor de qualquer tipo pode ser tratado como um `object`. Cada tipo no C#, direta ou indiretamente, deriva do tipo de classe `object`, e `object` é a classe base definitiva de todos os tipos. Os valores de tipos de referência são tratados como objetos simplesmente exibindo os valores como tipo `object`. Os valores de tipos de valor são tratados como objetos, executando *conversão boxing* e *operações de conversão unboxing*. No exemplo a seguir, um valor `int` é convertido em `object` e volta novamente ao `int`.

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Quando um valor de um tipo de valor é atribuído a `object` uma referência, uma "caixa" é alocada para conter o valor. Essa caixa é uma instância de um tipo de referência, e o valor é copiado para essa caixa. Por outro lado, quando uma `object` referência é convertida em um tipo de valor, é feita uma verificação de `object` que a referência é uma caixa do tipo de valor correto. Se a verificação for realizada com sucesso, o valor na caixa será copiado para o tipo de valor.

O sistema de tipos unificados do C# significa efetivamente que os `object` tipos de valor são tratados como referências "sob demanda". Devido à unificação, as bibliotecas de uso geral que usam `object` o tipo podem ser usadas com todos os tipos `object`que derivam de, incluindo tipos de referência e tipos de valor.

Existem vários tipos de *variáveis* no C#, incluindo campos, elementos de matriz, variáveis locais e parâmetros. As variáveis representam os locais de armazenamento e cada variável tem um tipo que determina quais valores podem ser armazenados na variável, conforme mostrado abaixo.

- Tipo de valor não nulo
  - Um valor de tipo exato
- Tipos de valor anulável
  - Um valor `null` ou um valor do tipo exato
- objeto
  - Uma referência `null`, uma referência a um objeto de qualquer tipo de referência ou uma referência a um valor de qualquer tipo de valor demarcado
- Tipo de classe
  - Uma referência `null`, uma referência a uma instância desse tipo de classe ou uma referência a uma instância de uma classe derivada desse tipo de classe
- Tipo de interface
  - Uma referência `null`, uma referência a uma instância de um tipo de classe que implementa esse tipo de interface ou uma referência a um valor demarcado de um tipo de valor que implementa esse tipo de interface
- Tipo de matriz
  - Uma referência `null`, uma referência a uma instância desse tipo de matriz ou uma referência a uma instância de um tipo de matriz compatível
- Tipo delegado
  - Uma referência `null` ou uma referência a uma instância de um tipo de delegado compatível

> [!div class="step-by-step"]
> [Anterior](program-structure.md)
> [próximo](expressions.md)
