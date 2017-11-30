---
title: "Executando operações de cadeia de caracteres que não levam em conta a cultura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e703e9adc531b7d1695d3e9bbed61a2c0f62ad31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="performing-culture-insensitive-string-operations"></a>Executando operações de cadeia de caracteres que não levam em conta a cultura
A maioria dos métodos do .NET Framework que executam operações de cadeia de caracteres sensíveis à cultura por padrão fornecem sobrecargas de método que permitem que você especifique explicitamente a cultura a ser usado para passar um <xref:System.Globalization.CultureInfo> parâmetro. Essas sobrecargas permitem que você eliminar variações culturais no caso de mapeamentos e classificar as regras e garante resultados não levam em conta a cultura.  
  
 Esta seção fornece os seguintes tópicos para demonstrar como executar operações de cadeia de caracteres de cultura usando métodos do .NET Framework que são sensíveis à cultura por padrão.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Executando comparações de cadeias de caracteres que não levam em conta a cultura](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 Descreve como usar o <xref:System.String.Compare%2A?displayProperty=nameWithType> e <xref:System.String.CompareTo%2A?displayProperty=nameWithType> métodos para executar comparações de cadeia de caracteres de cultura.  
  
 [Executando alterações de maiúsculas e minúsculas que não levam em conta a cultura](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 Descreve como usar o <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, e <xref:System.Char.ToLower%2A?displayProperty=nameWithType> métodos para realizar alterações não levam em conta a cultura.  
  
 [Executando operações de cadeia de caracteres que não levam em conta a cultura em coleções](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 Descreve como usar o <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> classe <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> e <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> para executar operações não levam em conta a cultura em coleções.  
  
 [Executando operações de cadeia de caracteres que não levam em conta a cultura em matrizes](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 Descreve como usar o <xref:System.Array.Sort%2A?displayProperty=nameWithType> e <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> métodos para executar operações não levam em conta a cultura em matrizes.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Operações de cadeia de caracteres que não levam em conta a cultura](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 Descreve por que você deve estar ciente da cultura ao executar operações em cadeias de caracteres e fornece diretrizes para quando executar operações sensíveis à cultura e quando executar operações não levam em conta a cultura.
