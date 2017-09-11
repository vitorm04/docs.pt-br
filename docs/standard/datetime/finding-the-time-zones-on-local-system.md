---
title: "Encontrando os fusos horários definidos em um sistema local"
description: "Encontrando os fusos horários definidos em um sistema local"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3a6ee323-f3cf-486d-aa0c-103931f1eba9
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: e61017e2a0e26295c3be7e8265674b1a5d2ae5a3
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="finding-the-time-zones-defined-on-a-local-system"></a><span data-ttu-id="2bc4e-104">Encontrando os fusos horários definidos em um sistema local</span><span class="sxs-lookup"><span data-stu-id="2bc4e-104">Finding the time zones defined on a local system</span></span>

<span data-ttu-id="2bc4e-105">A classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) não expõe um construtor público.</span><span class="sxs-lookup"><span data-stu-id="2bc4e-105">The [System.TimeZoneInfo](xref:System.TimeZoneInfo) class does not expose a public constructor.</span></span> <span data-ttu-id="2bc4e-106">Como resultado, a palavra-chave `new` não pode ser usada para criar um novo objeto [TimeZoneInfo](xref:System.TimeZoneInfo).</span><span class="sxs-lookup"><span data-stu-id="2bc4e-106">As a result, the `new` keyword cannot be used to create a new [TimeZoneInfo](xref:System.TimeZoneInfo) object.</span></span> <span data-ttu-id="2bc4e-107">Em vez disso, objetos [TimeZoneInfo](xref:System.TimeZoneInfo) são instanciados por meio da recuperação de informações sobre fusos horários predefinidos do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="2bc4e-107">Instead, [TimeZoneInfo](xref:System.TimeZoneInfo) objects are instantiated by retrieving information on predefined time zones from the operating system.</span></span> <span data-ttu-id="2bc4e-108">Este tópico discute a instanciação de um fuso horário dos dados armazenados pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="2bc4e-108">This topic discusses instantiating a time zone from data stored by the operating system.</span></span> <span data-ttu-id="2bc4e-109">Além disso, `static` (`Shared` no Visual Basic) propriedades da classe [TimeZoneInfo](xref:System.TimeZoneInfo) fornecem acesso ao UTC (Tempo Universal Coordenado) e ao fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="2bc4e-109">In addition, `static` (`Shared` in Visual Basic) properties of the [TimeZoneInfo](xref:System.TimeZoneInfo) class provide access to Coordinated Universal Time (UTC) and the local time zone.</span></span>

## <a name="accessing-individual-time-zones"></a><span data-ttu-id="2bc4e-110">Acessando fusos horários individuais</span><span class="sxs-lookup"><span data-stu-id="2bc4e-110">Accessing Individual Time Zones</span></span>

<span data-ttu-id="2bc4e-111">A classe [TimeZoneInfo](xref:System.TimeZoneInfo) fornece dois objetos de fuso horário predefinidos que representam o horário UTC e o fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="2bc4e-111">The [TimeZoneInfo](xref:System.TimeZoneInfo) class provides two predefined time zone objects that represent the UTC time and the local time zone.</span></span> <span data-ttu-id="2bc4e-112">Eles estão disponíveis nas propriedades [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) e [TimeZoneInfo](xref:System.TimeZoneInfo.Local), respectivamente.</span><span class="sxs-lookup"><span data-stu-id="2bc4e-112">They are available from the [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) and [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) properties, respectively.</span></span> <span data-ttu-id="2bc4e-113">Para obter instruções sobre como acessar o UTC ou fusos horários locais, veja [Como acessar os objetos de fuso horário UTC e local predefinidos](access-utc-and-local.md).</span><span class="sxs-lookup"><span data-stu-id="2bc4e-113">For instructions on accessing the UTC or local time zones, see [How to: access the predefined UTC and local time zone objects](access-utc-and-local.md).</span></span> 

<span data-ttu-id="2bc4e-114">Você também pode instanciar um objeto [TimeZoneInfo](xref:System.TimeZoneInfo) que representa qualquer fuso horário definido pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="2bc4e-114">You can also instantiate a [TimeZoneInfo](xref:System.TimeZoneInfo) object that represents any time zone defined by the operating system.</span></span> <span data-ttu-id="2bc4e-115">Para obter instruções sobre como instanciar um objeto de fuso horário específico, veja [Como criar uma instância de um objeto TimeZoneInfo](instantiate-time-zone-info.md).</span><span class="sxs-lookup"><span data-stu-id="2bc4e-115">For instructions on instantiating a specific time zone object, see [How to: instantiate a TimeZoneInfo object](instantiate-time-zone-info.md).</span></span>

## <a name="time-zone-identifiers"></a><span data-ttu-id="2bc4e-116">Identificadores de fuso horário</span><span class="sxs-lookup"><span data-stu-id="2bc4e-116">Time Zone Identifiers</span></span>

<span data-ttu-id="2bc4e-117">O identificador do fuso horário é um campo de chave que identifica exclusivamente o fuso horário.</span><span class="sxs-lookup"><span data-stu-id="2bc4e-117">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="2bc4e-118">Enquanto a maioria das chaves são relativamente curtas, o identificador de fuso horário é comparativamente longo.</span><span class="sxs-lookup"><span data-stu-id="2bc4e-118">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="2bc4e-119">Na maioria dos casos, seu valor corresponde ao da propriedade [TimeZoneInfo.StandardName](xref:System.TimeZoneInfo.StandardName), que é usada para fornecer o nome da hora padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="2bc4e-119">In most cases, its value corresponds to the [TimeZoneInfo.StandardName](xref:System.TimeZoneInfo.StandardName) property, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="2bc4e-120">No entanto, há exceções.</span><span class="sxs-lookup"><span data-stu-id="2bc4e-120">However, there are exceptions.</span></span> <span data-ttu-id="2bc4e-121">A melhor maneira de certificar-se de que você forneça um identificador válido é enumerar os fusos horários disponíveis no sistema e observar os identificadores associados.</span><span class="sxs-lookup"><span data-stu-id="2bc4e-121">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note their associated identifiers.</span></span> <span data-ttu-id="2bc4e-122">Para obter instruções sobre como enumerar os fusos horários, veja [Como enumerar os fusos horários presentes em um computador](enumerate-time-zones.md).</span><span class="sxs-lookup"><span data-stu-id="2bc4e-122">For instructions on enumerating time zones, see [How to: enumerate time zones present on a computer](enumerate-time-zones.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2bc4e-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2bc4e-123">See Also</span></span>

[<span data-ttu-id="2bc4e-124">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="2bc4e-124">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="2bc4e-125">Como acessar os objetos de fuso horário predefinidos UTC e local</span><span class="sxs-lookup"><span data-stu-id="2bc4e-125">How to: access the predefined UTC and local time zone objects</span></span>](access-utc-and-local.md)

[<span data-ttu-id="2bc4e-126">Como criar uma instância de um objeto TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="2bc4e-126">How to: instantiate a TimeZoneInfo object</span></span>](instantiate-time-zone-info.md)

[<span data-ttu-id="2bc4e-127">Como enumerar os fusos horários presentes em um computador</span><span class="sxs-lookup"><span data-stu-id="2bc4e-127">How to: enumerate time zones present on a computer</span></span>](enumerate-time-zones.md)

[<span data-ttu-id="2bc4e-128">Convertendo horários entre fusos horários</span><span class="sxs-lookup"><span data-stu-id="2bc4e-128">Converting times between time zones</span></span>](converting-between-time-zones.md)
