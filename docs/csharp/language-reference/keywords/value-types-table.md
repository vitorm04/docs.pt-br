---
title: Tabela de tipos de valor – Referência em C#
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: 2475f63099e47beedc610b8815a8e39e1f7be77e
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611211"
---
# <a name="value-types-table-c-reference"></a>Tabela de tipos de valor (Referência em C#)

A tabela a seguir mostra os tipos de valor de C#:

|Tipo de valor|Categoria|Sufixo de tipo|
|----------------|--------------|-----------------|
|[bool](bool.md)|Boolean||
|[byte](byte.md)|Não assinado, numérico, [integral](integral-types-table.md)||
|[char](char.md)|Não assinado, numérico, [integral](integral-types-table.md)||
|[decimal](decimal.md)|Numérico, [ponto flutuante](floating-point-types-table.md)|M ou m|
|[double](double.md)|Numérico, [ponto flutuante](floating-point-types-table.md)|D ou d|
|[enum](enum.md)|Enumeração||
|[float](float.md)|Numérico, [ponto flutuante](floating-point-types-table.md)|F ou f|
|[int](int.md)|Assinado, numérico, [integral](integral-types-table.md)||
|[long](long.md)|Assinado, numérico, [integral](integral-types-table.md)|L ou l|
|[sbyte](sbyte.md)|Assinado, numérico, [integral](integral-types-table.md)||
|[short](short.md)|Assinado, numérico, [integral](integral-types-table.md)||
|[struct](struct.md)|Estrutura definida pelo usuário||
|[uint](uint.md)|Não assinado, numérico, [integral](integral-types-table.md)|U ou u|
|[ulong](ulong.md)|Não assinado, numérico, [integral](integral-types-table.md)|UL, Ul, uL, ul, LU, Lu, lU ou lu|
|[ushort](ushort.md)|Não assinado, numérico, [integral](integral-types-table.md)||

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
- [Tabelas de referência de tipos](reference-tables-for-types.md)
- [Tabela de valores padrão](default-values-table.md)
- [Tipos de valor](value-types.md)
- [Tabela de formatação de resultados numéricos](formatting-numeric-results-table.md)