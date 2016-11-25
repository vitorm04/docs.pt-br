---
title: "Tabelas de conversão de tipos"
description: "Tabelas de conversão de tipos"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d602f260-e7cf-49c8-a37f-731f40e4a538
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 16f38150f26b477de5685d2d3b0ef18afb94c236

---

# <a name="type-conversion-tables"></a>Tabelas de conversão de tipos

Conversões de expansão ocorrem quando um valor de um tipo é convertido em outro tipo de tamanho igual ou maior. Conversões de redução ocorrem quando um valor de um tipo é convertido em um valor de outro tipo de tamanho menor. As tabelas neste tópico ilustram os comportamentos exibidos por ambos os tipos de conversões.

## <a name="widening-conversions"></a>Conversões de expansão

Tipo | Pode ser convertido sem perda de dados para
---- | -------------------------------------
[Byte](xref:System.Byte) | [UInt16](xref:System.UInt16), [Int16](xref:System.Int16), [UInt32](xref:System.UInt32), [Int32](xref:System.Int32), [UInt64](xref:System.UInt64), [Int64](xref:System.Int64), [Simples](xref:System.Single), [Duplo](xref:System.Double), [Decimal](xref:System.Decimal)
[SByte](xref:System.SByte) | [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [Simples](xref:System.Single), [Duplo](xref:System.Double), [Decimal](xref:System.Decimal)
[Int16](xref:System.Int16) | [Int32](xref:System.Int32), [Int64](xref:System.Int64), [Simples](xref:System.Single), [Duplo](xref:System.Double), [Decimal](xref:System.Decimal)
[UInt16](xref:System.UInt16) | [UInt32](xref:System.UInt32), [Int32](xref:System.Int32), [UInt64](xref:System.UInt64), [Int64](xref:System.Int64), [Simples](xref:System.Single), [Duplo](xref:System.Double), [Decimal](xref:System.Decimal)
[Char](xref:System.Char) | [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [Int32](xref:System.Int32), [UInt64](xref:System.UInt64), [Int64](xref:System.Int64), [Simples](xref:System.Single), [Duplo](xref:System.Double), [Decimal](xref:System.Decimal)
[Int32](xref:System.Int32) | [Int64](xref:System.Int64), [Duplo](xref:System.Double), [Decimal](xref:System.Decimal)
[UInt32](xref:System.UInt32) | [Int64](xref:System.Int64), [UInt64](xref:System.UInt64), [Duplo](xref:System.Double), [Decimal](xref:System.Decimal)
[Int64](xref:System.Int64) | [Decimal](xref:System.Decimal)
[UInt64](xref:System.UInt64) | [Decimal](xref:System.Decimal)
[Simples](xref:System.Single) | [Duplo](xref:System.Double)

Algumas conversões de expansão para [Simples](xref:System.Single) ou [Duplo](xref:System.Double) podem causar perda de precisão. A tabela a seguir descreve as conversões de expansão que, às vezes, resultam em perda de informações.

Tipo | Pode ser convertido para
---- | -------------------
[Int32](xref:System.Int32) | [Simples](xref:System.Single)
[UInt32](xref:System.UInt32) | [Simples](xref:System.Single)
[Int64](xref:System.Int64) | [Simples](xref:System.Single), [Duplo](xref:System.Double)
[UInt64](xref:System.UInt64) | [Simples](xref:System.Single), [Duplo](xref:System.Double)
[Decimal](xref:System.Decimal) | [Simples](xref:System.Single), [Duplo](xref:System.Double)

## <a name="narrowing-conversions"></a>Conversões de redução

Uma conversão de redução para [Simples](xref:System.Single) ou [Duplo](xref:System.Double) pode causar perda de informações. Se o tipo de destino não puder expressar corretamente a magnitude da origem, o tipo resultante será definido como a constante `PositiveInfinity` ou `NegativeInfinity`. `PositiveInfinity` resulta da divisão de um número positivo por zero e também é retornado quando o valor de um [Simples](xref:System.Single) ou [Duplo](xref:System.Double) ultrapassar o valor do `MaxValue` campo. `NegativeInfinity` resulta da divisão de um número negativo por zero e também é retornado quando o valor de um [Simples](xref:System.Single) ou [Duplo](xref:System.Double) for inferior ao valor do `MinValue` campo. Uma conversão de um [Duplo](xref:System.Double) para um [Simples](xref:System.Single) pode resultar em `PositiveInfinity` ou `NegativeInfinity`.

Uma conversão de redução também pode resultar em perda de informações para outros tipos de dados. No entanto, [OverflowException](xref:System.OverflowException) será lançada se o valor de um tipo que está sendo convertido estiver fora do intervalo especificado pelos campos `MaxValue` e `MinValue` do tipo de destino e a conversão será verificada pelo tempo de execução para garantir que o valor do tipo de destino não ultrapasse `MaxValue` ou `MinValue`. Conversões executadas com a classe [System.Convert](xref:System.Convert) sempre são verificadas dessa maneira.

A tabela a seguir lista conversões que lançam [OverflowException](xref:System.OverflowException) usando [System.Convert](xref:System.Convert) ou qualquer conversão selecionada se o valor do tipo que está sendo convertido estiver fora do intervalo definido pelo tipo resultante.

Tipo | Pode ser convertido para
---- | -------------------
[Byte](xref:System.Byte) | [SByte](xref:System.SByte)
[SByte](xref:System.SByte) | [Byte](xref:System.Byte), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64)
[Int16](xref:System.Int16) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [UInt16](xref:System.UInt16)
[UInt16](xref:System.UInt16) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16)
[Int32](xref:System.Int32) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32)
[UInt32](xref:System.UInt32) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [UInt16](xref:System.UInt16), [Int32](xref:System.Int32)
[Int64](xref:System.Int64) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [UInt16](xref:System.UInt16), [Int32](xref:System.Int32), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64)
[UInt64](xref:System.UInt64) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [UInt16](xref:System.UInt16), [Int32](xref:System.Int32), [UInt32](xref:System.UInt32), [Int64](xref:System.Int64)
[Decimal](xref:System.Decimal) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [UInt16](xref:System.UInt16), [Int32](xref:System.Int32), [UInt32](xref:System.UInt32), [Int64](xref:System.Int64), [UInt64](xref:System.UInt64)
[Simples](xref:System.Single) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [UInt16](xref:System.UInt16), [Int32](xref:System.Int32), [UInt32](xref:System.UInt32), [Int64](xref:System.Int64), [UInt64](xref:System.UInt64)
[Duplo](xref:System.Double) | [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [UInt16](xref:System.UInt16), [Int32](xref:System.Int32), [UInt32](xref:System.UInt32), [Int64](xref:System.Int64), [UInt64](xref:System.UInt64)

## <a name="see-also"></a>Consulte também

[System.Convert](xref:System.Convert)

[Conversão de Tipos](type-conversion.md)




<!--HONumber=Nov16_HO3-->


