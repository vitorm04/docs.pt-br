---
title: 'Como: acessar os objetos de fuso horário predefinidos UTC e local'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET], retrieving
- time zones [.NET], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
ms.openlocfilehash: 598cd631fab1ddc115bc6153580351b1dc14d5bf
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063879"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="2df0e-102">Como: acessar os objetos de fuso horário predefinidos UTC e local</span><span class="sxs-lookup"><span data-stu-id="2df0e-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="2df0e-103">A <xref:System.TimeZoneInfo> classe fornece duas propriedades <xref:System.TimeZoneInfo.Utc%2A> e <xref:System.TimeZoneInfo.Local%2A> , que dão ao seu código acesso a objetos de fuso horário predefinidos.</span><span class="sxs-lookup"><span data-stu-id="2df0e-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="2df0e-104">Este tópico discute como acessar os objetos <xref:System.TimeZoneInfo> retornados por essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="2df0e-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="2df0e-105">Para acessar o objeto TimeZoneInfo de UTC (Tempo Universal Coordenado)</span><span class="sxs-lookup"><span data-stu-id="2df0e-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="2df0e-106">Use a `static` `Shared` Propriedade (em Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> para acessar o tempo universal coordenado.</span><span class="sxs-lookup"><span data-stu-id="2df0e-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="2df0e-107">Em vez de atribuir o <xref:System.TimeZoneInfo> objeto retornado pela propriedade a uma variável de objeto, continue acessando o tempo universal coordenado por meio da <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="2df0e-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="2df0e-108">Para acessar o fuso horário local</span><span class="sxs-lookup"><span data-stu-id="2df0e-108">To access the local time zone</span></span>

1. <span data-ttu-id="2df0e-109">Use a `static` `Shared` Propriedade (em Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> para acessar o fuso horário do sistema local.</span><span class="sxs-lookup"><span data-stu-id="2df0e-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="2df0e-110">Em vez de atribuir o <xref:System.TimeZoneInfo> objeto retornado pela propriedade a uma variável de objeto, continue a acessar o fuso horário local por meio da <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="2df0e-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="2df0e-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2df0e-111">Example</span></span>

<span data-ttu-id="2df0e-112">O código a seguir usa <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> as <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Propriedades e para converter uma hora do fuso horário padrão do leste dos EUA e do Canadá, bem como para exibir o nome do fuso horário para o console do.</span><span class="sxs-lookup"><span data-stu-id="2df0e-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="2df0e-113">Você sempre deve acessar o fuso horário local por meio da <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriedade em vez de atribuir o fuso horário local a uma <xref:System.TimeZoneInfo> variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="2df0e-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="2df0e-114">Da mesma forma, você sempre deve acessar o tempo universal coordenado por meio da <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriedade em vez de atribuir a zona UTC a uma <xref:System.TimeZoneInfo> variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="2df0e-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="2df0e-115">Isso impede que a <xref:System.TimeZoneInfo> variável de objeto seja invalidada por uma chamada para o <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="2df0e-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="2df0e-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="2df0e-116">Compiling the code</span></span>

<span data-ttu-id="2df0e-117">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="2df0e-117">This example requires:</span></span>

- <span data-ttu-id="2df0e-118">Que o <xref:System> namespace seja importado com a `using` instrução (necessária no código C#).</span><span class="sxs-lookup"><span data-stu-id="2df0e-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="2df0e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2df0e-119">See also</span></span>

- [<span data-ttu-id="2df0e-120">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="2df0e-120">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="2df0e-121">Encontrando os fusos horários definidos em um sistema local</span><span class="sxs-lookup"><span data-stu-id="2df0e-121">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="2df0e-122">Como criar uma instância de um objeto TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="2df0e-122">How to: Instantiate a TimeZoneInfo object</span></span>](instantiate-time-zone-info.md)
