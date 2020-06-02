---
title: Datas, horas e fusos horários
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zone objects [.NET Framework]
- date and time data [.NET Framework]
- time zones [.NET Framework]
- times [.NET Framework], time zones
- time [.NET Framework], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
ms.openlocfilehash: 86602cd6e662b1b1057832247babc558ef67b79f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276927"
---
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="9c29a-102">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="9c29a-102">Dates, times, and time zones</span></span>

<span data-ttu-id="9c29a-103">Além da estrutura <xref:System.DateTime> básica, o .NET fornece as seguintes classes que dão suporte para trabalhar com fusos horários:</span><span class="sxs-lookup"><span data-stu-id="9c29a-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="9c29a-104">Use esta classe para trabalhar com o fuso horário local do sistema e a zona UTC (Tempo Universal Coordenado).</span><span class="sxs-lookup"><span data-stu-id="9c29a-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.</span></span> <span data-ttu-id="9c29a-105">A funcionalidade da <xref:System.TimeZone> classe é amplamente substituída pela <xref:System.TimeZoneInfo> classe.</span><span class="sxs-lookup"><span data-stu-id="9c29a-105">The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="9c29a-106">Use essa classe para trabalhar com qualquer fuso horário que esteja predefinido em um sistema, para criar novos fusos horários e para converter facilmente datas e horas de um fuso horário para outro.</span><span class="sxs-lookup"><span data-stu-id="9c29a-106">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="9c29a-107">Para novos desenvolvimentos, use a classe <xref:System.TimeZoneInfo> em vez da classe <xref:System.TimeZone>.</span><span class="sxs-lookup"><span data-stu-id="9c29a-107">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="9c29a-108">Use essa estrutura para trabalhar com datas e horas cujo deslocamento (ou diferença) em relação ao horário UTC é conhecido.</span><span class="sxs-lookup"><span data-stu-id="9c29a-108">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="9c29a-109">A estrutura <xref:System.DateTimeOffset> combina um valor de data e hora com o deslocamento desse horário em relação ao UTC.</span><span class="sxs-lookup"><span data-stu-id="9c29a-109">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="9c29a-110">Devido à sua relação com o UTC, um valor individual de data e hora identifica, sem ambiguidade um único ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="9c29a-110">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="9c29a-111">Isso aumenta a portabilidade de um computador para outro de um valor de <xref:System.DateTimeOffset> em relação a um valor de <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="9c29a-111">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="9c29a-112">Esta seção da documentação fornece as informações de que você precisa para trabalhar com fusos horários e para criar aplicativos com reconhecimento de fuso horário que podem converter datas e horas de um fuso horário para outro.</span><span class="sxs-lookup"><span data-stu-id="9c29a-112">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9c29a-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="9c29a-113">In this section</span></span>

<span data-ttu-id="9c29a-114">[Visão geral sobre fuso horário](time-zone-overview.md) Aborda a terminologia, os conceitos e as questões envolvidas na criação de aplicativos com reconhecimento de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9c29a-114">[Time zone overview](time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="9c29a-115">[Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](choosing-between-datetime.md) Discute quando usar os <xref:System.DateTime> <xref:System.DateTimeOffset> tipos, e <xref:System.TimeZoneInfo> ao trabalhar com dados de data e hora.</span><span class="sxs-lookup"><span data-stu-id="9c29a-115">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="9c29a-116">[Encontrando os fusos horários definidos em um sistema local](finding-the-time-zones-on-local-system.md) Descreve como enumerar os fusos horários encontrados em um sistema local.</span><span class="sxs-lookup"><span data-stu-id="9c29a-116">[Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="9c29a-117">[Como enumerar os fusos horários presentes em um computador](enumerate-time-zones.md) Fornece exemplos que enumeram os fusos horários definidos no Registro de um computador e que permitem que os usuários selecionem um fuso horário predefinido em uma lista.</span><span class="sxs-lookup"><span data-stu-id="9c29a-117">[How to: Enumerate time zones present on a computer](enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="9c29a-118">[Como acessar os objetos de fuso horário UTC e local predefinidos](access-utc-and-local.md) Descreve como acessar o Tempo Universal Coordenado e o fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="9c29a-118">[How to: Access the predefined UTC and local time zone objects](access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="9c29a-119">[Como criar uma instância de um objeto TimeZoneInfo](instantiate-time-zone-info.md) Descreve como criar uma instância de um objeto <xref:System.TimeZoneInfo> do Registro do sistema local.</span><span class="sxs-lookup"><span data-stu-id="9c29a-119">[How to: Instantiate a TimeZoneInfo object](instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="9c29a-120">[Criando uma instância de um objeto DateTimeOffset](instantiating-a-datetimeoffset-object.md) Discute as maneiras de criar uma instância de um objeto <xref:System.DateTimeOffset> e maneiras de converter um valor <xref:System.DateTime> em um valor <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="9c29a-120">[Instantiating a DateTimeOffset object](instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="9c29a-121">[Como criar fusos horários sem regras de ajuste](create-time-zones-without-adjustment-rules.md) Descreve como criar um fuso horário personalizado sem suporte para transição de/para o horário de verão.</span><span class="sxs-lookup"><span data-stu-id="9c29a-121">[How to: Create time zones without adjustment rules](create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="9c29a-122">[Como criar fusos horários com regras de ajuste](create-time-zones-with-adjustment-rules.md) Descreve como criar um fuso horário personalizado com suporte a uma ou mais transições de/para o horário de verão.</span><span class="sxs-lookup"><span data-stu-id="9c29a-122">[How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="9c29a-123">[Salvando e restaurando fusos horários](saving-and-restoring-time-zones.md) Descreve o suporte de <xref:System.TimeZoneInfo> para serialização e desserialização dos dados de fuso horário e ilustra alguns dos cenários nos quais esses recursos podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="9c29a-123">[Saving and restoring time zones](saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="9c29a-124">[Como salvar fusos horários em um recurso inserido](save-time-zones-to-an-embedded-resource.md) Descreve como criar um fuso horário personalizado e salvar suas informações em um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="9c29a-124">[How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="9c29a-125">[Como restaurar fusos horários de um recurso inserido](restore-time-zones-from-an-embedded-resource.md) Descreve como criar instâncias de fusos horários personalizados que foram salvos em um arquivo de recurso inserido.</span><span class="sxs-lookup"><span data-stu-id="9c29a-125">[How to: Restore time zones from an embedded resource](restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="9c29a-126">[Executando operações aritméticas com datas e horas](performing-arithmetic-operations.md) Discute os problemas envolvidos ao adicionar, subtrair e comparar valores <xref:System.DateTime> e <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="9c29a-126">[Performing arithmetic operations with dates and times](performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="9c29a-127">[Como usar fusos horários em aritmética de data e hora](use-time-zones-in-arithmetic.md) Descreve como realizar uma aritmética de data e hora que reflita as regras de ajuste de um fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9c29a-127">[How to: Use time zones in date and time arithmetic](use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="9c29a-128">[Convertendo entre DateTime e DateTimeOffset](converting-between-datetime-and-offset.md) Descreve como converter entre valores <xref:System.DateTime> e <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="9c29a-128">[Converting between DateTime and DateTimeOffset](converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="9c29a-129">[Convertendo horários entre fusos horários](converting-between-time-zones.md) Descreve como converter horários de um fuso horário para outro.</span><span class="sxs-lookup"><span data-stu-id="9c29a-129">[Converting times between time zones](converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="9c29a-130">[Como resolver horários ambíguos](resolve-ambiguous-times.md) Descreve como resolver um horário ambíguo, mapeando-o para o horário padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9c29a-130">[How to: Resolve ambiguous times](resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="9c29a-131">[Como permitir que os usuários resolvam horários ambíguos](let-users-resolve-ambiguous-times.md) Descreve como permitir que um usuário determine o mapeamento entre uma hora local ambígua e o Tempo Universal Coordenado.</span><span class="sxs-lookup"><span data-stu-id="9c29a-131">[How to: Let users resolve ambiguous times](let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="9c29a-132">Referência</span><span class="sxs-lookup"><span data-stu-id="9c29a-132">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
