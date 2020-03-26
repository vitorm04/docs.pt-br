---
title: Tipos de estrutura - Referência C#
ms.date: 02/24/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: b126706ff9c881e5c2d5cc7ee4833ac8896e3fcc
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507237"
---
# <a name="structure-types-c-reference"></a>Tipos de estrutura (referência C#)

Um *tipo de estrutura* (ou tipo de *estrutura)* é um tipo de [valor](value-types.md) que pode encapsular dados e funcionalidades relacionadas. Você usa `struct` a palavra-chave para definir um tipo de estrutura:

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

Os tipos de estrutura têm *semântica de valor.* Ou seja, uma variável de um tipo de estrutura contém uma instância do tipo. Por padrão, os valores variáveis são copiados na atribuição, passando um argumento para um método e retornando um resultado do método. No caso de uma variável do tipo estrutura, uma instância do tipo é copiada. Para obter mais informações, consulte [Tipos de valor](value-types.md).

Normalmente, você usa tipos de estrutura para projetar pequenos tipos centrados em dados que fornecem pouco ou nenhum comportamento. Por exemplo, .NET usa tipos de estrutura para representar um número [(inteiro](integral-numeric-types.md) e [real),](floating-point-numeric-types.md)um [valor booleano,](bool.md)um [caractere Unicode,](char.md)uma [instância de tempo](xref:System.DateTime). Se você está focado no comportamento de um tipo, considere definir uma [classe.](../keywords/class.md) Os tipos de classe têm *semântica de referência.* Ou seja, uma variável de um tipo de classe contém uma referência a uma instância do tipo, não à instância em si.

## <a name="limitations-with-the-design-of-a-structure-type"></a>Limitações com o design de um tipo de estrutura

Quando você projeta um tipo de estrutura, você tem os mesmos recursos que com um tipo [de classe,](../keywords/class.md) com as seguintes exceções:

- Você não pode declarar um construtor sem parâmetros. Cada tipo de estrutura já fornece um construtor implícito sem parâmetros que produz o [valor padrão](default-values.md) do tipo.

- Você não pode inicializar um campo de instância ou propriedade em sua declaração. No entanto, você pode inicializar um campo [estático](../keywords/static.md) ou [const](../keywords/const.md) ou uma propriedade estática em sua declaração.

- Um construtor de um tipo de estrutura deve inicializar todos os campos de instância do tipo.

- Um tipo de estrutura não pode herdar de outra classe ou tipo de estrutura e não pode ser a base de uma classe. No entanto, um tipo de estrutura pode implementar [interfaces.](../keywords/interface.md)

- Você não pode declarar um [finalizador](../../programming-guide/classes-and-structs/destructors.md) dentro de um tipo de estrutura.

## <a name="instantiation-of-a-structure-type"></a>Instantiva de um tipo de estrutura

Em C#, você deve inicializar uma variável declarada antes que ela possa ser usada. Como uma variável do `null` tipo de estrutura não pode ser (a menos que seja uma variável de um tipo de [valor anulado),](nullable-value-types.md)você deve instanciar uma instância do tipo correspondente. Há várias maneiras de fazer isso.

Normalmente, você instancia um tipo de estrutura [`new`](../operators/new-operator.md) ligando para um construtor apropriado com o operador. Cada tipo de estrutura tem pelo menos um construtor. É um construtor implícito sem parâmetros, que produz o [valor padrão](default-values.md) do tipo. Você também pode usar uma [expressão de valor padrão](../operators/default.md) para produzir o valor padrão de um tipo.

Se todos os campos de exemplo de um tipo de `new` estrutura estiverem acessíveis, você também poderá instancia-lo sem o operador. Nesse caso, você deve inicializar todos os campos de instância antes do primeiro uso da instância. O seguinte exemplo mostra como fazer isso:

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

No caso dos [tipos de valor embutidos,](value-types.md#built-in-value-types)use os literais correspondentes para especificar um valor do tipo.

## <a name="passing-structure-type-variables-by-reference"></a>Passando variáveis de tipo de estrutura por referência

Quando você passa uma variável de tipo de estrutura para um método como argumento ou retorna um valor de tipo de estrutura a partir de um método, toda a instância de um tipo de estrutura é copiada. Isso pode afetar o desempenho do seu código em cenários de alto desempenho que envolvem grandes tipos de estrutura. Você pode evitar a cópia de valor passando uma variável tipo de estrutura por referência. Use [`ref`](../keywords/ref.md#passing-an-argument-by-reference)os [`out`](../keywords/out-parameter-modifier.md)modificadores do parâmetro , ou [`in`](../keywords/in-parameter-modifier.md) método para indicar que um argumento deve ser aprovado por referência. Use [o retorno do ref](../../programming-guide/classes-and-structs/ref-returns.md) para retornar um resultado do método por referência. Para obter mais informações, consulte [Escrever código C# seguro e eficiente](../../write-safe-efficient-code.md).

## <a name="conversions"></a>Conversões

Para qualquer tipo de estrutura, existem conversões <xref:System.ValueType?displayProperty=nameWithType> de <xref:System.Object?displayProperty=nameWithType> boxe [e unboxing](../../programming-guide/types/boxing-and-unboxing.md) para e de e tipos. Existem também conversões de boxe e unboxing entre um tipo de estrutura e qualquer interface que implemente.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, consulte a seção [Structs](~/_csharplang/spec/structs.md) da [especificação do idioma C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Diretrizes de design - Escolha entre classe e estrutura](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Diretrizes de design - Projeto de estrutura](../../../standard/design-guidelines/struct.md)
- [Classes e structs](../../programming-guide/classes-and-structs/index.md)
