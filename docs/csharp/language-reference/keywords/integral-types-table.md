---
title: Tabela de tipos integrais – Referência em C#
ms.custom: seodec18
description: Visão geral dos tipos integrais em C# internos
ms.date: 08/20/2018
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
ms.assetid: 62e86126-46ff-40b0-9028-e61d7558268c
ms.openlocfilehash: 1815f057e5cf26d64e5ff151f161cc56214efc1b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237981"
---
# <a name="integral-types-table-c-reference"></a>Tabela de tipos integrais (Referência em C#)

A tabela a seguir mostra os tamanhos e os intervalos de tipos integrais, que constituem um subconjunto de tipos simples.  
  
|Tipo|Intervalo|Tamanho|  
|----------|-----------|----------|  
|[sbyte](sbyte.md)|-128 a 127|Inteiro de 8 bits com sinal|  
|[byte](byte.md)|0 a 255|Inteiro de 8 bits sem sinal|  
|[char](char.md)|U+0000 a U+ffff|Caractere Unicode de 16 bits|  
|[short](short.md)|-32.768 a 32.767|Inteiro de 16 bits com sinal|  
|[ushort](ushort.md)|0 a 65.535|Inteiro de 16 bits sem sinal|  
|[int](int.md)|-2.147.483.648 a 2.147.483.647|Inteiro de 32 bits com sinal|  
|[uint](uint.md)|0 a 4.294.967.295|Inteiro de 32 bits sem sinal|  
|[long](long.md)|-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807|Inteiro de 64 bits com sinal|  
|[ulong](ulong.md)|0 a 18.446.744.073.709.551.615|Inteiro de 64 bits sem sinal|  

## <a name="remarks"></a>Comentários
  
Se o valor representado por um literal inteiro exceder <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilador [CS1021](../../misc/cs1021.md).

Use a classe <xref:System.Numerics.BigInteger?displayProperty=nameWithType> para representar um inteiro com sinal arbitrariamente grande.
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Tabelas de referência de tipos](reference-tables-for-types.md)
- [Tabela de tipos de ponto flutuante](floating-point-types-table.md)
- [Tabela de valores padrão](default-values-table.md)
- [Tabela de formatação de resultados numéricos](formatting-numeric-results-table.md)
- [Tabela de tipos internos](built-in-types-table.md)
