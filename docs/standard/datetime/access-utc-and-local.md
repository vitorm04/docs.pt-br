---
title: Como acessar o UTC predefinido e os objetos de fuso horário local
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
ms.openlocfilehash: ef22753d9934a52d955412a4493b608f265519aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132600"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="2af83-102">Como acessar o UTC predefinido e os objetos de fuso horário local</span><span class="sxs-lookup"><span data-stu-id="2af83-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="2af83-103">A classe <xref:System.TimeZoneInfo> fornece duas propriedades, <xref:System.TimeZoneInfo.Utc%2A> e <xref:System.TimeZoneInfo.Local%2A>, que dão ao seu código acesso a objetos de fuso horário predefinidos.</span><span class="sxs-lookup"><span data-stu-id="2af83-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="2af83-104">Este tópico discute como acessar os objetos <xref:System.TimeZoneInfo> retornados por essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="2af83-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="2af83-105">Para acessar o objeto TimeZoneInfo de UTC (Tempo Universal Coordenado)</span><span class="sxs-lookup"><span data-stu-id="2af83-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="2af83-106">Use a propriedade `static` (`Shared` na Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> para acessar o tempo universal coordenado.</span><span class="sxs-lookup"><span data-stu-id="2af83-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="2af83-107">Em vez de atribuir o objeto de <xref:System.TimeZoneInfo> retornado pela propriedade a uma variável de objeto, continue acessando o tempo universal coordenado por meio da propriedade <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2af83-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="2af83-108">Para acessar o fuso horário local</span><span class="sxs-lookup"><span data-stu-id="2af83-108">To access the local time zone</span></span>

1. <span data-ttu-id="2af83-109">Use a propriedade `static` (`Shared` na Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> para acessar o fuso horário do sistema local.</span><span class="sxs-lookup"><span data-stu-id="2af83-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="2af83-110">Em vez de atribuir o objeto de <xref:System.TimeZoneInfo> retornado pela propriedade a uma variável de objeto, continue acessando o fuso horário local por meio da propriedade <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2af83-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="2af83-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2af83-111">Example</span></span>

<span data-ttu-id="2af83-112">O código a seguir usa as propriedades <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> e <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> para converter uma hora do fuso horário padrão do leste dos EUA e Canadá, bem como para exibir o nome do fuso horário para o console do.</span><span class="sxs-lookup"><span data-stu-id="2af83-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="2af83-113">Você sempre deve acessar o fuso horário local por meio da propriedade <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> em vez de atribuir o fuso horário local a uma variável de objeto <xref:System.TimeZoneInfo>.</span><span class="sxs-lookup"><span data-stu-id="2af83-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="2af83-114">Da mesma forma, você sempre deve acessar o tempo universal coordenado por meio da propriedade <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> em vez de atribuir a zona UTC a uma variável de objeto <xref:System.TimeZoneInfo>.</span><span class="sxs-lookup"><span data-stu-id="2af83-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="2af83-115">Isso impede que a variável de objeto <xref:System.TimeZoneInfo> seja invalidada por uma chamada para o método <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2af83-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="2af83-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="2af83-116">Compiling the code</span></span>

<span data-ttu-id="2af83-117">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="2af83-117">This example requires:</span></span>

- <span data-ttu-id="2af83-118">Que o namespace <xref:System> seja importado com a instrução `using` ( C# obrigatória no código).</span><span class="sxs-lookup"><span data-stu-id="2af83-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="2af83-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2af83-119">See also</span></span>

- [<span data-ttu-id="2af83-120">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="2af83-120">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="2af83-121">Encontrando os fusos horários definidos em um sistema local</span><span class="sxs-lookup"><span data-stu-id="2af83-121">Finding the time zones defined on a local system</span></span>](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="2af83-122">Como criar uma instância de um objeto TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="2af83-122">How to: Instantiate a TimeZoneInfo object</span></span>](../../../docs/standard/datetime/instantiate-time-zone-info.md)
