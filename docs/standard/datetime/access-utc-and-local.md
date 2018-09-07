---
title: 'Como: acessar os objetos de fuso horário UTC e local predefinidos'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f074e6f6d9b11cc7d7405adced3a4523a31676fa
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086907"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Como: acessar os objetos de fuso horário UTC e local predefinidos

O <xref:System.TimeZoneInfo> classe fornece duas propriedades, <xref:System.TimeZoneInfo.Utc%2A> e <xref:System.TimeZoneInfo.Local%2A>, que dão acesso de código para objetos de fuso horário predefinido. Este tópico discute como acessar os objetos <xref:System.TimeZoneInfo> retornados por essas propriedades.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Para acessar o objeto TimeZoneInfo de UTC (Tempo Universal Coordenado)

1. Use o `static` (`Shared` no Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriedade para acessar o tempo Universal Coordenado.

2. Em vez de atribuir o <xref:System.TimeZoneInfo> objeto retornado pela propriedade a uma variável de objeto, continuar a acessar o tempo Universal Coordenado através de <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriedade.

### <a name="to-access-the-local-time-zone"></a>Para acessar o fuso horário local

1. Use o `static` (`Shared` no Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriedade para acessar o fuso horário local.

2. Em vez de atribuir o <xref:System.TimeZoneInfo> objeto retornado pela propriedade a uma variável de objeto, continuar a acessar o fuso horário local por meio de <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriedade.

## <a name="example"></a>Exemplo

O código a seguir usa o <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> e <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriedades para converter uma hora do fuso horário dos EUA e padrão do Leste do Canadá, bem como para exibir o nome do fuso horário no console.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Você deve sempre acessar o fuso horário local por meio de <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriedade em vez de atribuir a hora local da zona para um <xref:System.TimeZoneInfo> variável de objeto. Da mesma forma, você deve sempre acessar tempo Universal Coordenado através de <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriedade em vez de atribuir o UTC de zona para um <xref:System.TimeZoneInfo> variável de objeto. Isso impede que o <xref:System.TimeZoneInfo> variável de objeto do seja invalidada por uma chamada para o <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> método.

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

* Que uma referência à dll seja adicionada ao projeto.

* Que o <xref:System> namespace sejam importados com o `using` instrução (necessária em código c#).

## <a name="see-also"></a>Consulte também

* [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
* [Encontrando os fusos horários definidos em um sistema local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
* [Como criar uma instância de um objeto TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
