---
title: Tipos Básicos
description: Descobrir os tipos básicos fundamentais que são usados no F# idioma.
ms.date: 07/09/2018
ms.openlocfilehash: 74a276792e2566b8f18b87f4bdcfb923b713b9c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959103"
---
# <a name="basic-types"></a>Tipos básicos

Este tópico lista os tipos básicos que são definidos no F# idioma. Esses tipos são mais fundamental no F#, que formam a base para quase todos F# programa. Eles são um subconjunto de tipos primitivos do .NET.

|Tipo|Tipo .NET|Descrição|
|----|---------|-----------|
|`bool`|<xref:System.Boolean>|Os valores possíveis são `true` e `false`.|
|`byte`|<xref:System.Byte>|Valores de 0 a 255.|
|`sbyte`|<xref:System.SByte>|Valores de -128 a 127.|
|`int16`|<xref:System.Int16>|Valores de -32768 a 32767.|
|`uint16`|<xref:System.UInt16>|Valores de 0 a 65535.|
|`int`|<xref:System.Int32>|Valores de -2.147.483.648 a 2.147.483.647.|
|`uint32`|<xref:System.UInt32>|Valores de 0 a 4.294.967.295.|
|`int64`|<xref:System.Int64>|Valores de -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807.|
|`uint64`|<xref:System.UInt64>|Valores de 0 a 18.446.744.073.709.551.615.|
|`nativeint`|<xref:System.IntPtr>|Um ponteiro nativo como um inteiro com sinal.|
|`unativeint`|<xref:System.UIntPtr>|Um ponteiro nativo como um inteiro sem sinal.|
|`char`|<xref:System.Char>|Valores de caractere Unicode.|
|`string`|<xref:System.String>|Texto Unicode.|
|`decimal`|<xref:System.Decimal>|Tipo de dados que tem pelo menos 28 dígitos significativos de ponto flutuante.|
|`unit`|não aplicável|Indica a ausência de um valor real. O tipo tem apenas um valor formal, que é denotado `()`. O valor de unidade, `()`, geralmente é usado como um espaço reservado em que um valor é necessário, mas nenhum valor real está disponível ou faz sentido.|
|`void`|<xref:System.Void>|Não indica que nenhum tipo ou valor.|
|`float32`, `single`|<xref:System.Single>|Um tipo de ponto flutuante de 32 bits.|
|`float`, `double`|<xref:System.Double>|Um tipo de ponto flutuante de 64 bits.|

> [!NOTE]
> Você pode executar cálculos com números inteiros grandes demais para o tipo de inteiro de 64 bits usando o [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) tipo. `bigint` não é considerado um tipo básico; ele é uma abreviação de `System.Numerics.BigInteger`.

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)