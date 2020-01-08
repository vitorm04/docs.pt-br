---
title: Tipos de enumeração C# -referência
description: Saiba mais C# sobre tipos de enumeração que representam uma opção ou uma combinação de opções
ms.date: 12/13/2019
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
- enum type [C#]
- enumeration type [C#]
- bit flags [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 72bc867bf0a789279da9a01f97c85d96b78684ed
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75444343"
---
# <a name="enumeration-types-c-reference"></a>Tipos de enumeraçãoC# (referência)

Um tipo de enumeração (ou tipo de enumeração) é um tipo de valor definido por um conjunto de constantes nomeadas do tipo [numérico integral](integral-numeric-types.md) subjacente. Para definir um tipo de enumeração, use a palavra-chave `enum` e especifique os nomes dos *membros de enumeração*:

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

Por padrão, os valores constantes associados de membros de enumeração são do tipo `int`; Eles começam com zero e aumentam em um seguindo a ordem de texto de definição. Você pode especificar explicitamente qualquer outro tipo [numérico integral](integral-numeric-types.md) como um tipo subjacente de um tipo de enumeração. Você também pode especificar explicitamente os valores constantes associados, como mostra o exemplo a seguir:

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

Você não pode definir um método dentro da definição de um tipo de enumeração. Para adicionar funcionalidade a um tipo de enumeração, crie um [método de extensão](../../programming-guide/classes-and-structs/extension-methods.md).

O valor padrão de um tipo de enumeração `E` é o valor produzido pelo Expression `(E)0`, mesmo se zero não tiver o membro enum correspondente.

Você usa um tipo de enumeração para representar uma escolha de um conjunto de valores mutuamente exclusivos ou uma combinação de opções. Para representar uma combinação de opções, defina um tipo de enumeração como sinalizadores de bits.

## <a name="enumeration-types-as-bit-flags"></a>Tipos de Enumeração como Sinalizadores de Bit

Se você quiser que um tipo de enumeração represente uma combinação de opções, defina membros de enum para essas opções, de modo que uma opção individual seja um campo de bits. Ou seja, os valores associados desses membros de enumeração devem ser as potências de dois. Em seguida, você pode usar os [operadores lógicos de bits bit a `|` ou `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) para combinar opções ou combinações de interseção de opções, respectivamente. Para indicar que um tipo de enumeração declara campos de bits, aplique o atributo [flags](xref:System.FlagsAttribute) a ele. Como mostra o exemplo a seguir, você também pode incluir algumas combinações típicas na definição de um tipo de enumeração.

[!code-csharp[enum flags](~/samples/csharp/language-reference/builtin-types/EnumType.cs#Flags)]

Para obter mais informações e exemplos, consulte a página de referência da API <xref:System.FlagsAttribute?displayProperty=nameWithType> e os [Membros não exclusivos e a seção de atributo flags](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) da página de referência da API <xref:System.Enum?displayProperty=nameWithType>.

## <a name="the-systemenum-type-and-enum-constraint"></a>O tipo System. Enum e a restrição enum

O tipo de <xref:System.Enum?displayProperty=nameWithType> é a classe base abstrata de todos os tipos de enumeração. Ele fornece vários métodos para obter informações sobre um tipo de enumeração e seus valores. Para obter mais informações e exemplos, consulte a página de referência da API <xref:System.Enum?displayProperty=nameWithType>.

A partir C# do 7,3, você pode usar `System.Enum` em uma restrição de classe base (que é conhecida como [restrição de enumeração](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) para especificar que um parâmetro de tipo é um tipo de enumeração.

## <a name="conversions"></a>Conversões

Para qualquer tipo de enumeração, existem conversões explícitas entre o tipo de enumeração e seu tipo integral subjacente. Se você [converter](../operators/type-testing-and-cast.md#cast-operator-) um valor de enumeração para seu tipo subjacente, o resultado será o valor integral associado de um membro de enumeração.

[!code-csharp[enum conversions](~/samples/csharp/language-reference/builtin-types/EnumType.cs#Conversions)]

Use o método <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> para determinar se um tipo de enumeração contém um membro enum com determinado valor associado.

Para qualquer tipo de enumeração, existem conversões [boxing e unboxing](../../programming-guide/types/boxing-and-unboxing.md) de e para o tipo <xref:System.Enum?displayProperty=nameWithType>, respectivamente.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Enums](~/_csharplang/spec/enums.md)
- [Operações e valores de enum](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [Operadores lógicos de enumeração](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [Operadores de comparação de enumeração](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [Conversões de enumeração explícitas](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [Conversões implícitas de enumeração](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a>Veja também

- [Referência de C#](../index.md)
- [Cadeias de caracteres de formato de enumeração](../../../standard/base-types/enumeration-format-strings.md)
- [Convenções de nomenclatura de enumeração](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [instrução switch](../keywords/switch.md)
