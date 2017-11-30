---
title: Tipos primitivos (F#)
description: "Descobre os tipos primitivos fundamentais que são usados na linguagem F #."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f23d98b-551b-4fd2-9f4f-0fd7254288ed
ms.openlocfilehash: b493cdf7116d94f66940d03b86e584bcecbbb0f1
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2017
---
# <a name="primitive-types"></a>Tipos primitivos

Este tópico lista os tipos primitivos fundamentais que são usados na linguagem F #. Ele também fornece os tipos .NET correspondentes e os valores mínimos e máximos para cada tipo.

## <a name="summary-of-primitive-types"></a>Resumo de tipos primitivos
A tabela a seguir resume as propriedades de tipos F # primitivos.

|Tipo|Tipo .NET|Descrição|
|----|---------|-----------|
|`bool`|`System.Boolean`|Os valores possíveis são `true` e `false`.|
|`byte`|`System.Byte`|Valores de 0 a 255.|
|`sbyte`|`System.SByte`|Valores de -128 a 127.|
|`int16`|`System.Int16`|Valores de -32768 e 32767.|
|`uint16`|`System.UInt16`|Valores de 0 a 65535.|
|`int`|`System.Int32`|Valores de -2.147.483.648 a 2.147.483.647.|
|`uint32`|`System.UInt32`|Valores entre 0 e 4.294.967.295.|
|`int64`|`System.Int64`|Valores de -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807.|
|`uint64`|`System.UInt64`|Valores de 0 a 18.446.744.073.709.551.615.|
|`nativeint`|`System.IntPtr`|Um ponteiro nativo como um inteiro com sinal.|
|`unativeint`|`System.UIntPtr`|Um ponteiro nativo como um inteiro não assinado.|
|`char`|`System.Char`|Valores de caractere Unicode.|
|`string`|`System.String`|Texto Unicode.|
|`decimal`|`System.Decimal`|Um ponto flutuante tipo de dados que tenha pelo menos 28 os dígitos significativos.|
|`unit`|não aplicável|Indica a ausência de um valor real. O tipo tem apenas um valor formal, que é indicado `()`. O valor unitário, `()`, geralmente é usada como um espaço reservado em que um valor é necessário, mas nenhum valor real está disponível ou faz sentido.|
|`void`|`System.Void`|Não indica que nenhum tipo ou valor.|
|`float32, single`|`System.Single`|Um tipo de ponto flutuante de 32 bits.|
|`float, double`|`System.Double`|Um tipo de ponto flutuante de 64 bits.|

>[!NOTE]
Você pode executar cálculos com números inteiros muito grandes para o tipo de inteiro de 64 bits usando o [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) tipo. `bigint`não é considerado um tipo primitivo; é uma abreviação de `System.Numerics.BigInteger`.

## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)
