---
title: Tabela de tipos de valor – Referência em C#
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: 2e2897ff647140b58b3a1812e153a44a6fcdaef7
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859567"
---
# <a name="value-types-table-c-reference"></a>Tabela de tipos de valor (Referência em C#)

A tabela a seguir mostra os tipos de valor de C#:

|Tipo de valor|Categoria|Sufixo de tipo|
|----------------|--------------|-----------------|
|[bool](bool.md)|Boolean||
|`byte`|Não assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)||
|[char](char.md)|Não assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)
|`decimal`|Numérico, [ponto flutuante](../builtin-types/floating-point-numeric-types.md)|M ou m|
|`double`|Numérico, [ponto flutuante](../builtin-types/floating-point-numeric-types.md)|D ou d|
|[enum](enum.md)|Enumeração||
|`float`|Numérico, [ponto flutuante](../builtin-types/floating-point-numeric-types.md)|F ou f|
|`int`|Assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)||
|`long`|Assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)|L ou l|
|`sbyte`|Assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)||
|`short`|Assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)||
|[struct](struct.md)|Estrutura definida pelo usuário||
|`uint`|Não assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)|U ou u|
|`ulong`|Não assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)|UL, Ul, uL, ul, LU, Lu, lU ou lu|
|`ushort`|Não assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)||

## <a name="remarks"></a>Comentários

Você pode usar um sufixo de tipo para especificar um tipo de um literal numérico. Por exemplo:

```csharp
decimal a = 0.1M;
```

Se um [literal numérico inteiro](~/_csharplang/spec/lexical-structure.md#integer-literals) não tiver sufixo, seu tipo será o primeiro dos tipos a seguir em que seu valor pode ser representado: `int`, `uint`, `long`, `ulong`.

Se um [literal numérico real](~/_csharplang/spec/lexical-structure.md#real-literals) não tiver sufixo, ele será do tipo `double`.

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Tabela de valores padrão](default-values-table.md)
- [Tipos de valor](value-types.md)
- [Tabela de formatação de resultados numéricos](formatting-numeric-results-table.md)
