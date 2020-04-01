---
title: Como analisar cadeias de caracteres no .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: 717022e5d2e292c1624e6155bd7571e4daa997b9
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523809"
---
# <a name="parsing-strings-in-net"></a>Como analisar cadeias de caracteres no .NET
Uma operação de análise converte uma cadeia de caracteres que representa um tipo base .NET em tal tipo base. Por exemplo, uma operação de análise é usada para converter uma cadeia de caracteres em um número de ponto flutuante ou em um valor de data e hora. O método usado com mais frequência para executar uma operação de análise é o método `Parse`. Como a análise é a operação inversa da formatação (que envolve a conversão de um tipo base em sua representação de cadeia de caracteres), muitas das mesmas regras e convenções se aplicam. Assim como a formatação usa um objeto que implementa a interface <xref:System.IFormatProvider> para fornecer informações de formatação que diferenciam a cultura, a análise também usa um objeto que implementa a interface <xref:System.IFormatProvider> para determinar como interpretar uma representação de cadeia de caracteres. Para obter mais informações, consulte [Tipos de formatação](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Analisar cadeias de caracteres numéricas](../../../docs/standard/base-types/parsing-numeric.md)  
 Descreve como converter cadeias de caracteres em tipos numéricos do .NET.  
  
 [Analisar cadeias de caracteres de Data e Hora](../../../docs/standard/base-types/parsing-datetime.md)  
 Descreve como converter cadeias de caracteres em tipos **DateTime** do .NET.  
  
 [Analisando outras cadeias de caracteres](../../../docs/standard/base-types/parsing-other.md)  
 Descreve como converter cadeias de caracteres em tipos **Char**, **Boolean** e **Enum**.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Formatar tipos](../../../docs/standard/base-types/formatting-types.md)  
 Descreve conceitos básicos de formatação, como especificadores de formato e provedores de formato.  
  
 [Conversão de tipo no .NET](../../../docs/standard/base-types/type-conversion.md)  
 Descreve como converter tipos.
