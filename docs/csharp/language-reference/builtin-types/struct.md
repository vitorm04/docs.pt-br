---
title: Tipos de estrutura C# -referência
ms.date: 02/24/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 6113912f176d2d7b68c77ff2e78a361b373ca31a
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634865"
---
# <a name="structure-types-c-reference"></a>Tipos de estruturaC# (referência)

Um *tipo de estrutura* (ou *tipo de struct*) é um tipo de [valor](value-types.md) que pode encapsular dados e funcionalidade relacionada. Você usa a palavra-chave `struct` para definir um tipo de estrutura:

[!code-csharp[struct example](~/samples/csharp/language-reference/builtin-types/StructType.cs#StructExample)]

Os tipos de estrutura têm *semântica de valor*. Ou seja, uma variável de um tipo de estrutura contém uma instância do tipo. Por padrão, os valores de variáveis são copiados na atribuição, passando um argumento para um método e retornando um resultado de método. No caso de uma variável de tipo de estrutura, uma instância do tipo é copiada. Para obter mais informações, consulte [tipos de valor](value-types.md).

Normalmente, você usa tipos de estrutura para criar pequenos tipos centrados em dados que fornecem pouco ou nenhum comportamento. Por exemplo, o .NET usa tipos de estrutura para representar um número ( [inteiro](integral-numeric-types.md) e [real](floating-point-numeric-types.md)), um [valor booliano](bool.md), um [caractere Unicode](char.md), uma [instância de tempo](xref:System.DateTime). Se você estiver concentrado no comportamento de um tipo, considere definir uma [classe](../keywords/class.md). Os tipos de classe têm *semânticas de referência*. Ou seja, uma variável de um tipo de classe contém uma referência a uma instância do tipo, não a instância em si.

## <a name="limitations-with-the-design-of-a-structure-type"></a>Limitações com o design de um tipo de estrutura

Ao criar um tipo de estrutura, você tem os mesmos recursos que com um tipo de [classe](../keywords/class.md) , com as seguintes exceções:

- Você não pode declarar um construtor sem parâmetros. Cada tipo de estrutura já fornece um Construtor implícito sem parâmetros que produz o [valor padrão](default-values.md) do tipo.

- Não é possível inicializar um campo ou propriedade de instância em sua declaração. No entanto, você pode inicializar um campo [estático](../keywords/static.md) ou [const](../keywords/const.md) ou uma propriedade estática em sua declaração.

- Um construtor de um tipo de estrutura deve inicializar todos os campos de instância do tipo.

- Um tipo de estrutura não pode herdar de outra classe ou tipo de estrutura e não pode ser a base de uma classe. No entanto, um tipo de estrutura pode implementar [interfaces](../keywords/interface.md).

- Você não pode declarar um [finalizador](../../programming-guide/classes-and-structs/destructors.md) em um tipo de estrutura.

## <a name="instantiation-of-a-structure-type"></a>Instanciação de um tipo de estrutura

No C#, você deve inicializar uma variável declarada antes de poder ser usada. Como uma variável de tipo de estrutura não pode ser `null` (a menos que seja uma variável de um [tipo de valor anulável](nullable-value-types.md)), você deve criar uma instância do tipo correspondente. Há várias maneiras de fazer isso.

Normalmente, você cria uma instância de um tipo de estrutura chamando um construtor apropriado com o operador de [`new`](../operators/new-operator.md) . Cada tipo de estrutura tem pelo menos um construtor. Esse é um Construtor implícito sem parâmetros, que produz o [valor padrão](default-values.md) do tipo. Você também pode usar o operador [padrão](../operators/default.md) ou o literal para produzir o valor padrão de um tipo.

Se todos os campos de instância de um tipo de estrutura estiverem acessíveis, você também poderá instanciá-lo sem o operador de `new`. Nesse caso, você deve inicializar todos os campos de instância antes do primeiro uso da instância. O seguinte exemplo mostra como fazer isso:

[!code-csharp[without new](~/samples/csharp/language-reference/builtin-types/StructType.cs#WithoutNew)]

No caso dos tipos de [valor internos](value-types.md#built-in-value-types), use os literais correspondentes para especificar um valor do tipo.

## <a name="passing-structure-type-variables-by-reference"></a>Passando variáveis de tipo de estrutura por referência

Quando você passa uma variável de tipo de estrutura para um método como um argumento ou retorna um valor de tipo de estrutura de um método, toda a instância de um tipo de estrutura é copiada. Isso pode afetar o desempenho do seu código em cenários de alto desempenho que envolvem tipos de estrutura grandes. Você pode evitar a cópia de valor passando uma variável de tipo de estrutura por referência. Use os modificadores de parâmetro do método [`ref`](../keywords/ref.md#passing-an-argument-by-reference), [`out`](../keywords/out-parameter-modifier.md)ou [`in`](../keywords/in-parameter-modifier.md) para indicar que um argumento deve ser passado por referência. Use [ref retorna](../../programming-guide/classes-and-structs/ref-returns.md) para retornar um resultado de método por referência. Para obter mais informações, consulte [escrever código seguro C# e eficiente](../../write-safe-efficient-code.md).

## <a name="conversions"></a>Conversões

Para qualquer tipo de estrutura, existem conversões [boxing e unboxing](../../programming-guide/types/boxing-and-unboxing.md) de e para os tipos <xref:System.ValueType?displayProperty=nameWithType> e <xref:System.Object?displayProperty=nameWithType>. Existem também conversões boxing e unboxing entre um tipo de estrutura e qualquer interface que ela implementa.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, consulte a seção [structs](~/_csharplang/spec/structs.md) da [ C# especificação da linguagem](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Confira também

- [Referência de C#](../index.md)
- [Diretrizes de design-escolhendo entre classe e estrutura](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Diretrizes de design – design de struct](../../../standard/design-guidelines/struct.md)
- [Classes e structs](../../programming-guide/classes-and-structs/index.md)
