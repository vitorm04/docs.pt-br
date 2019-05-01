---
title: 'Como: acessar os objetos de fuso horário predefinidos UTC e local'
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
ms.openlocfilehash: c10c07c08a4e676cf3c84a5722814eaed85f74a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026591"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="fb651-102">Como: acessar os objetos de fuso horário predefinidos UTC e local</span><span class="sxs-lookup"><span data-stu-id="fb651-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="fb651-103">O <xref:System.TimeZoneInfo> classe fornece duas propriedades, <xref:System.TimeZoneInfo.Utc%2A> e <xref:System.TimeZoneInfo.Local%2A>, que dão acesso de código para objetos de fuso horário predefinido.</span><span class="sxs-lookup"><span data-stu-id="fb651-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="fb651-104">Este tópico discute como acessar os objetos <xref:System.TimeZoneInfo> retornados por essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="fb651-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="fb651-105">Para acessar o objeto TimeZoneInfo de UTC (Tempo Universal Coordenado)</span><span class="sxs-lookup"><span data-stu-id="fb651-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="fb651-106">Use o `static` (`Shared` no Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriedade para acessar o tempo Universal Coordenado.</span><span class="sxs-lookup"><span data-stu-id="fb651-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="fb651-107">Em vez de atribuir o <xref:System.TimeZoneInfo> objeto retornado pela propriedade a uma variável de objeto, continuar a acessar o tempo Universal Coordenado através de <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="fb651-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="fb651-108">Para acessar o fuso horário local</span><span class="sxs-lookup"><span data-stu-id="fb651-108">To access the local time zone</span></span>

1. <span data-ttu-id="fb651-109">Use o `static` (`Shared` no Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriedade para acessar o fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="fb651-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="fb651-110">Em vez de atribuir o <xref:System.TimeZoneInfo> objeto retornado pela propriedade a uma variável de objeto, continuar a acessar o fuso horário local por meio de <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="fb651-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="fb651-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb651-111">Example</span></span>

<span data-ttu-id="fb651-112">O código a seguir usa o <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> e <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriedades para converter uma hora do fuso horário dos EUA e padrão do Leste do Canadá, bem como para exibir o nome do fuso horário no console.</span><span class="sxs-lookup"><span data-stu-id="fb651-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="fb651-113">Você deve sempre acessar o fuso horário local por meio de <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriedade em vez de atribuir a hora local da zona para um <xref:System.TimeZoneInfo> variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="fb651-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="fb651-114">Da mesma forma, você deve sempre acessar tempo Universal Coordenado através de <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriedade em vez de atribuir o UTC de zona para um <xref:System.TimeZoneInfo> variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="fb651-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="fb651-115">Isso impede que o <xref:System.TimeZoneInfo> variável de objeto do seja invalidada por uma chamada para o <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="fb651-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="fb651-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="fb651-116">Compiling the code</span></span>

<span data-ttu-id="fb651-117">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="fb651-117">This example requires:</span></span>

* <span data-ttu-id="fb651-118">Que uma referência à dll seja adicionada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="fb651-118">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="fb651-119">Que o <xref:System> namespace sejam importados com o `using` instrução (necessária em código c#).</span><span class="sxs-lookup"><span data-stu-id="fb651-119">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb651-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb651-120">See also</span></span>

- [<span data-ttu-id="fb651-121">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="fb651-121">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="fb651-122">Encontrando os fusos horários definidos em um sistema local</span><span class="sxs-lookup"><span data-stu-id="fb651-122">Finding the time zones defined on a local system</span></span>](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="fb651-123">Como: Criar uma instância de um objeto TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="fb651-123">How to: Instantiate a TimeZoneInfo object</span></span>](../../../docs/standard/datetime/instantiate-time-zone-info.md)
