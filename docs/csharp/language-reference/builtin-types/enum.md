---
title: Tipos de enumeração - Referência C#
description: Saiba mais sobre os tipos de enumeração C# que representam uma escolha ou uma combinação de escolhas
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
ms.openlocfilehash: 15f5e9ccb1396277229ba935381812700f63ece8
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121151"
---
# <a name="enumeration-types-c-reference"></a>Tipos de enumeração (referência C#)

Um *tipo de enumeração* (ou *tipo enum)* é um tipo de [valor](value-types.md) definido por um conjunto de constantes nomeadas do tipo [numérico integral](integral-numeric-types.md) subjacente. Para definir um tipo de `enum` enumeração, use a palavra-chave e especifique os nomes dos membros do *enum:*

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

Por padrão, os valores constantes associados `int`dos membros enum são do tipo; eles começam com zero e aumentam por um seguindo a ordem de texto de definição. Você pode especificar explicitamente qualquer outro tipo [numérico integral](integral-numeric-types.md) como um tipo subjacente de um tipo de enumeração. Você também pode especificar explicitamente os valores constantes associados, como mostra o exemplo a seguir:

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

O valor padrão de um `E` tipo de enumeração é o valor produzido pela expressão, `(E)0`mesmo que zero não tenha o membro enum correspondente.

Você usa um tipo de enumeração para representar uma escolha de um conjunto de valores mutuamente exclusivos ou uma combinação de escolhas. Para representar uma combinação de opções, defina um tipo de enumeração como sinalizadores de bit.

## <a name="enumeration-types-as-bit-flags"></a>Tipos de Enumeração como Sinalizadores de Bit

Se você quiser que um tipo de enumeração represente uma combinação de escolhas, defina os membros do enum para essas escolhas de tal forma que uma escolha individual seja um pouco de campo. Ou seja, os valores associados desses membros do enum devem ser os poderes de dois. Em seguida, você pode usar os [operadores lógicos `|` bitwise ou `&` ](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) para combinar escolhas ou interceptar combinações de escolhas, respectivamente. Para indicar que um tipo de enumeração declara campos de bits, aplique o atributo [Sinalizadores](xref:System.FlagsAttribute) a ele. Como o exemplo a seguir mostra, você também pode incluir algumas combinações típicas na definição de um tipo de enumeração.

[!code-csharp[enum flags](snippets/EnumType.cs#Flags)]

Para obter mais informações e <xref:System.FlagsAttribute?displayProperty=nameWithType> exemplos, consulte a página de referência da API e os membros não exclusivos e a seção de [atributoS da](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) página de referência da <xref:System.Enum?displayProperty=nameWithType> API.

## <a name="the-systemenum-type-and-enum-constraint"></a>A restrição system.enum e enum

O <xref:System.Enum?displayProperty=nameWithType> tipo é a classe base abstrata de todos os tipos de enumeração. Ele fornece uma série de métodos para obter informações sobre um tipo de enumeração e seus valores. Para obter mais informações e <xref:System.Enum?displayProperty=nameWithType> exemplos, consulte a página de referência da API.

Começando com C# 7.3, `System.Enum` você pode usar em uma restrição de classe base (que é conhecida como [restrição de enum](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) para especificar que um parâmetro de tipo é um tipo de enumeração.

## <a name="conversions"></a>Conversões

Para qualquer tipo de enumeração, existem conversões explícitas entre o tipo de enumeração e seu tipo integral subjacente. Se você [lançar](../operators/type-testing-and-cast.md#cast-expression) um valor de enum para o seu tipo subjacente, o resultado é o valor integral associado de um membro enum.

[!code-csharp[enum conversions](snippets/EnumType.cs#Conversions)]

Use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> o método para determinar se um tipo de enumeração contém um membro enum com o determinado valor associado.

Para qualquer tipo de enumeração, existem conversões <xref:System.Enum?displayProperty=nameWithType> de boxe e [unboxing](../../programming-guide/types/boxing-and-unboxing.md) para e do tipo, respectivamente.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Enums](~/_csharplang/spec/enums.md)
- [Operações e valores de enum](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [Operadores lógicos de enumeração](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [Operadores de comparação de enumeração](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [Conversões explícitas de enumeração](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [Conversões implícitas de enumeração](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Cadeias de caracteres de formato de enumeração](../../../standard/base-types/enumeration-format-strings.md)
- [Diretrizes de design - Design enum](../../../standard/design-guidelines/enum.md)
- [Diretrizes de design - Convenções de nomeação enum](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [Instrução switch](../keywords/switch.md)
