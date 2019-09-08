---
title: Métodos de System.Convert
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: d0aa0b11223e23b874471962d727d8e16e152ceb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781051"
---
# <a name="systemconvert-methods"></a>Métodos de System.Convert

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não oferece suporte aos seguintes métodos de <xref:System.Convert> .

- Versões com um parâmetro de <xref:System.IFormatProvider> .

- Métodos que envolvem matrizes de char ou matrizes de bytes:

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- Os seguintes métodos:

  - `public static <Type2> To<Type2>(<Type1> value);` onde

    `Type1` e `Type2` são cada um de `sbyte`, `uint`, `ulong`, ou `ushort`.

  - C#:

    `int To<int type>(string value, int fromBase),`

    `ToString(... value, int toBase)`

  - Visual Basic:

    `Function To(Of [Numeric])(value as String, fromBase As Integer)`

    `As [Numeric], ToString( value As …, toBase As Integer)`

  - <xref:System.Convert.IsDBNull%2A>

  - <xref:System.Convert.GetTypeCode%2A>

  - <xref:System.Convert.ChangeType%2A>

## <a name="see-also"></a>Consulte também

- [Funções e tipos de dados](data-types-and-functions.md)
