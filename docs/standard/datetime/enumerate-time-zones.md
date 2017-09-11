---
title: "Como enumerar os fusos horários presentes em um computador"
description: "Como enumerar os fusos horários presentes em um computador"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c5ae4a6c-1790-4355-b5b1-879aaf956129
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f30ba2a483ff7e5867417969946c2774175d5e3d
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a><span data-ttu-id="fdae3-104">Como enumerar os fusos horários presentes em um computador</span><span class="sxs-lookup"><span data-stu-id="fdae3-104">How to: enumerate time zones present on a computer</span></span>

<span data-ttu-id="fdae3-105">Trabalhar com êxito com um fuso horário designado requer que informações sobre o fuso horário em questão estejam disponíveis no sistema.</span><span class="sxs-lookup"><span data-stu-id="fdae3-105">Successfully working with a designated time zone requires that information about that time zone be available to the system.</span></span> <span data-ttu-id="fdae3-106">Por exemplo, o sistema operacional Windows armazena essas informações no Registro.</span><span class="sxs-lookup"><span data-stu-id="fdae3-106">For example, the Windows operating system stores this information in the registry.</span></span> <span data-ttu-id="fdae3-107">Embora o número total de fusos horários existentes seja grande, o Registro contém informações apenas sobre um subconjunto deles.</span><span class="sxs-lookup"><span data-stu-id="fdae3-107">However, although the total number of time zones that exist throughout the world is large, the registry contains information about only a subset of them.</span></span> <span data-ttu-id="fdae3-108">Além disso, o Registro em si é uma estrutura dinâmica cujo conteúdo está sujeito a alterações deliberadas ou acidentais.</span><span class="sxs-lookup"><span data-stu-id="fdae3-108">In addition, the registry itself is a dynamic structure whose contents are subject to both deliberate and accidental change.</span></span> <span data-ttu-id="fdae3-109">Como resultado, um aplicativo nem sempre pode presumir que um determinado fuso horário esteja definido e disponível no sistema.</span><span class="sxs-lookup"><span data-stu-id="fdae3-109">As a result, an application cannot always assume that a particular time zone is defined and available on a system.</span></span> <span data-ttu-id="fdae3-110">A primeira etapa para muitos aplicativos que usam informações de fuso horário é determinar se os fusos horários necessários estão disponíveis no sistema local ou dar ao usuário uma lista dos fusos horários entre os quais escolher.</span><span class="sxs-lookup"><span data-stu-id="fdae3-110">The first step for many applications that use time zone information applications is to determine whether required time zones are available on the local system, or to give the user a list of time zones from which to select.</span></span> <span data-ttu-id="fdae3-111">Isso requer que o aplicativo enumere os fusos horários definidos no sistema local.</span><span class="sxs-lookup"><span data-stu-id="fdae3-111">This requires that an application enumerate the time zones defined on a local system.</span></span> 

## <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a><span data-ttu-id="fdae3-112">Para enumerar os fusos horários presentes no sistema local</span><span class="sxs-lookup"><span data-stu-id="fdae3-112">To enumerate the time zones present on the local system</span></span>

1. <span data-ttu-id="fdae3-113">Chame o método [TimeZoneInfo.GetSystemTimeZones](xref:System.TimeZoneInfo.GetSystemTimeZones).</span><span class="sxs-lookup"><span data-stu-id="fdae3-113">Call the [TimeZoneInfo.GetSystemTimeZones](xref:System.TimeZoneInfo.GetSystemTimeZones) method.</span></span> <span data-ttu-id="fdae3-114">O método retorna uma coleção [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) genérica de objetos [TimeZoneInfo](xref:System.TimeZoneInfo).</span><span class="sxs-lookup"><span data-stu-id="fdae3-114">The method returns a generic [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) collection of [TimeZoneInfo](xref:System.TimeZoneInfo) objects.</span></span> <span data-ttu-id="fdae3-115">As entradas na coleção são classificadas segundo a propriedade [DisplayName](xref:System.TimeZoneInfo.DisplayName).</span><span class="sxs-lookup"><span data-stu-id="fdae3-115">The entries in the collection are sorted by their [DisplayName](xref:System.TimeZoneInfo.DisplayName) property.</span></span> <span data-ttu-id="fdae3-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="fdae3-116">For example:</span></span>

    ```csharp
    ReadOnlyCollection<TimeZoneInfo> tzCollection;
    tzCollection = TimeZoneInfo.GetSystemTimeZones();
    ```

    ```vb
    Dim tzCollection As ReadOnlyCollection(Of TimeZoneInfo) = TimeZoneInfo.GetSystemTimeZones
    ```

2. <span data-ttu-id="fdae3-117">Enumere os objetos [TimeZoneInfo](xref:System.TimeZoneInfo) individuais na coleção usando um loop `foreach` (em C#) ou um loop `For Each…Next` (no Visual Basic) e execute o processamento que for necessário em cada objeto.</span><span class="sxs-lookup"><span data-stu-id="fdae3-117">Enumerate the individual [TimeZoneInfo](xref:System.TimeZoneInfo) objects in the collection by using a `foreach` loop (in C#) or a `For Each…Next` loop (in Visual Basic), and perform any necessary processing on each object.</span></span> <span data-ttu-id="fdae3-118">Por exemplo, o código a seguir enumera a coleção [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) dos objetos [TimeZoneInfo](xref:System.TimeZoneInfo) retornados na etapa 1 e lista o nome de exibição de cada fuso horário no console.</span><span class="sxs-lookup"><span data-stu-id="fdae3-118">For example, the following code enumerates the [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) collection of [TimeZoneInfo](xref:System.TimeZoneInfo) objects returned in step 1 and lists the display name of each time zone on the console.</span></span>

    ```csharp
    foreach (TimeZoneInfo timeZone in tzCollection)
    Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName);
    ```

    ```vb
    For Each timeZone As TimeZoneInfo In tzCollection
        Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName)
    Next
    ```

## <a name="see-also"></a><span data-ttu-id="fdae3-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fdae3-119">See Also</span></span>

[<span data-ttu-id="fdae3-120">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="fdae3-120">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="fdae3-121">Encontrando os fusos horários definidos em um sistema local</span><span class="sxs-lookup"><span data-stu-id="fdae3-121">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)


