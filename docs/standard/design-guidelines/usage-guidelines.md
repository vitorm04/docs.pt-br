---
title: Diretrizes de uso
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7bd54a2325c9721ad17943ba663e7ec0c300632e
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925070"
---
# <a name="usage-guidelines"></a>Diretrizes de uso

Esta seção contém diretrizes para usar tipos comuns em APIs publicamente acessíveis. Ele lida com o uso direto de tipos de estrutura (por exemplo, atributos de serialização) internas e operadores comuns de sobrecarga.
  
O <xref:System.IDisposable?displayProperty=nameWithType> interface não é abordada nesta seção, mas é discutida a [padrão de descarte](../../../docs/standard/design-guidelines/dispose-pattern.md) seção.

> [!NOTE]
> Para obter diretrizes e informações adicionais sobre o sobre outro comum, tipos internos do .NET Framework, consulte os tópicos de referência para o seguinte: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType>.

## <a name="in-this-section"></a>Nesta seção

[Matrizes](arrays.md)  
[Atributos](attributes.md)  
[Coleções](guidelines-for-collections.md)  
[Serialização](serialization.md)  
[Uso de System.XML](system-xml-usage.md)  
[Operadores de igualdade](equality-operators.md)  

*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*
  
## <a name="see-also"></a>Consulte também

[Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
