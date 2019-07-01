---
title: Tabela de tipos de valor – Referência em C#
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: 98829f30c2c25c0710cf3fe044359d3c7538fe76
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424048"
---
# <a name="value-types-table-c-reference"></a>Tabela de tipos de valor (Referência em C#)

A tabela a seguir mostra os tipos de valor de C#:

|Tipo de valor|Categoria|Sufixo de tipo|
|----------------|--------------|-----------------|
|[bool](bool.md)|Boolean||
|[byte](../builtin-types/integral-numeric-types.md)|Não assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)||
|[char](char.md)|Não assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)
)||
|[decimal](decimal.md)|Numérico, [ponto flutuante](floating-point-types-table.md)|M ou m|
|[double](double.md)|Numérico, [ponto flutuante](floating-point-types-table.md)|D ou d|
|[enum](enum.md)|Enumeração||
|[float](float.md)|Numérico, [ponto flutuante](floating-point-types-table.md)|F ou f|
|[int](../builtin-types/integral-numeric-types.md)|Assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)||
|[long](../builtin-types/integral-numeric-types.md)|Assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)|L ou l|
|[sbyte](../builtin-types/integral-numeric-types.md)|Assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)||
|[short](../builtin-types/integral-numeric-types.md)|Assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)||
|[struct](struct.md)|Estrutura definida pelo usuário||
|[uint](../builtin-types/integral-numeric-types.md)|Não assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)|U ou u|
|[ulong](../builtin-types/integral-numeric-types.md)|Não assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)|UL, Ul, uL, ul, LU, Lu, lU ou lu|
|[ushort](../builtin-types/integral-numeric-types.md)|Não assinado, numérico, [integral](../builtin-types/integral-numeric-types.md)||

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
