---
title: Como analisar cadeias de caracteres no .NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9c2193dd1b1f3c0478efb5fc9c2b80250ef1878f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="parsing-strings-in-net"></a>Como analisar cadeias de caracteres no .NET
Uma operação de análise converte uma cadeia de caracteres que representa um tipo base .NET em tal tipo base. Por exemplo, uma operação de análise é usada para converter uma cadeia de caracteres em um número de ponto flutuante ou em um valor de data e hora. O método usado com mais frequência para executar uma operação de análise é o método `Parse`. Como a análise é a operação inversa da formatação (que envolve a conversão de um tipo base em sua representação de cadeia de caracteres), muitas das mesmas regras e convenções se aplicam. Assim como a formatação usa um objeto que implementa a interface <xref:System.IFormatProvider> para fornecer informações de formatação que diferenciam a cultura, a análise também usa um objeto que implementa a interface <xref:System.IFormatProvider> para determinar como interpretar uma representação de cadeia de caracteres. Para obter mais informações, consulte [Tipos de formatação](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Analisando cadeias de caracteres numéricas](../../../docs/standard/base-types/parsing-numeric.md)  
 Descreve como converter cadeias de caracteres em tipos numéricos do .NET.  
  
 [Analisando cadeias de caracteres de data e hora](../../../docs/standard/base-types/parsing-datetime.md)  
 Descreve como converter cadeias de caracteres em tipos **DateTime** do .NET.  
  
 [Analisando outras cadeias de caracteres](../../../docs/standard/base-types/parsing-other.md)  
 Descreve como converter cadeias de caracteres em tipos **Char**, **Boolean** e **Enum**.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Formatando Tipos](../../../docs/standard/base-types/formatting-types.md)  
 Descreve conceitos básicos de formatação, como especificadores de formato e provedores de formato.  
  
 [Conversão de tipo no .NET](../../../docs/standard/base-types/type-conversion.md)  
 Descreve como converter tipos.  
  
 [Tipos base](../../../docs/standard/base-types/index.md)  
 Descreve as operações comuns que você pode executar em tipos de base do .NET.
