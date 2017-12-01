---
title: "Tabelas de conversão de tipos no .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- widening conversions
- narrowing conversions
- type conversion, table
- converting types, narrowing conversions
- converting types, widening conversions
- base types, converting
- tables [.NET Framework], type conversions
- data types [.NET Framework], converting
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 327469f9a151b6ef7e1c42f6669c0a9dae7016fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="type-conversion-tables-in-net"></a>Tabelas de conversão de tipos no .NET
Conversões de expansão ocorrem quando um valor de um tipo é convertido em outro tipo de tamanho igual ou maior. Conversões de redução ocorrem quando um valor de um tipo é convertido em um valor de outro tipo de tamanho menor. As tabelas neste tópico ilustram os comportamentos exibidos por ambos os tipos de conversões.  
  
## <a name="widening-conversions"></a>Conversões de expansão  
 A tabela a seguir descreve as conversões ampliadoras que podem ser executadas sem a perda de informações.  
  
|Tipo|Pode ser convertido sem perda de dados para|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.SByte>|<xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int16>|<xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt16>|<xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Char>|<xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int32>|<xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt32>|<xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 Algumas conversões de ampliação <xref:System.Single> ou <xref:System.Double> pode causar perda de precisão. A tabela a seguir descreve as conversões de expansão que, às vezes, resultam em perda de informações.  
  
|Tipo|Pode ser convertido para|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Conversões de redução  
 Uma conversão redutora para <xref:System.Single> ou <xref:System.Double> pode causar perda de informações. Se o tipo de destino não puder expressar corretamente a magnitude da origem, o tipo resultante será definido como a constante `PositiveInfinity` ou `NegativeInfinity`. `PositiveInfinity`resultados de divisão de um número positivo por zero e também é retornado quando o valor de um <xref:System.Single> ou <xref:System.Double> excede o valor da `MaxValue` campo. `NegativeInfinity`resultados de divisão por zero de um número negativo e também é retornado quando o valor de um <xref:System.Single> ou <xref:System.Double> cai abaixo do valor da `MinValue` campo. Uma conversão de um <xref:System.Double> para um <xref:System.Single> pode resultar em `PositiveInfinity` ou `NegativeInfinity`.  
  
 Uma conversão de redução também pode resultar em perda de informações para outros tipos de dados. No entanto, um <xref:System.OverflowException> é gerada se o valor de um tipo que está sendo convertido está fora do intervalo especificado, o tipo de destino `MaxValue` e `MinValue` campos e a conversão é verificada pelo tempo de execução para garantir que o valor de destino tipo não exceda seu `MaxValue` ou `MinValue`. Conversões executadas com a <xref:System.Convert?displayProperty=nameWithType> classe sempre são verificadas dessa maneira.  
  
 A tabela a seguir lista as conversões que lançam uma <xref:System.OverflowException> usando <xref:System.Convert?displayProperty=nameWithType> ou qualquer selecionada conversão se o valor do tipo que está sendo convertido estiver fora do intervalo definido pelo tipo resultante.  
  
|Tipo|Pode ser convertido para|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>|  
|<xref:System.Int16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16>|  
|<xref:System.UInt16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>|  
|<xref:System.Int32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32>|  
|<xref:System.UInt32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>|  
|<xref:System.Int64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64>|  
|<xref:System.UInt64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>|  
|<xref:System.Decimal>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Single>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Double>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Convert?displayProperty=nameWithType>  
 [Conversão de tipo no .NET](../../../docs/standard/base-types/type-conversion.md)
