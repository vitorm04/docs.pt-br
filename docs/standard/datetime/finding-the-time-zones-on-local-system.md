---
title: "Encontrando os fusos horários definidos em um sistema local"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c86932455301d15621c03d4440a8a16e44575bac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a><span data-ttu-id="89ca4-102">Encontrando os fusos horários definidos em um sistema local</span><span class="sxs-lookup"><span data-stu-id="89ca4-102">Finding the time zones defined on a local system</span></span>

<span data-ttu-id="89ca4-103">O <xref:System.TimeZoneInfo> classe expõe um construtor público.</span><span class="sxs-lookup"><span data-stu-id="89ca4-103">The <xref:System.TimeZoneInfo> class does not expose a public constructor.</span></span> <span data-ttu-id="89ca4-104">Como resultado, o `new` palavra-chave não pode ser usado para criar um novo <xref:System.TimeZoneInfo> objeto.</span><span class="sxs-lookup"><span data-stu-id="89ca4-104">As a result, the `new` keyword cannot be used to create a new <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="89ca4-105">Em vez disso, <xref:System.TimeZoneInfo> objetos são instanciados Recuperando informações sobre fusos horários predefinidos do registro ou por meio da criação de um fuso horário personalizado.</span><span class="sxs-lookup"><span data-stu-id="89ca4-105">Instead, <xref:System.TimeZoneInfo> objects are instantiated either by retrieving information on predefined time zones from the registry or by creating a custom time zone.</span></span> <span data-ttu-id="89ca4-106">Este tópico discute a instanciação de um fuso horário dos dados armazenados no registro.</span><span class="sxs-lookup"><span data-stu-id="89ca4-106">This topic discusses instantiating a time zone from data stored in the registry.</span></span> <span data-ttu-id="89ca4-107">Além disso, `static` (`shared` no Visual Basic) propriedades da <xref:System.TimeZoneInfo> classe fornecer acesso ao tempo Universal Coordenado (UTC) e o fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="89ca4-107">In addition, `static` (`shared` in Visual Basic) properties of the <xref:System.TimeZoneInfo> class provide access to Coordinated Universal Time (UTC) and the local time zone.</span></span>

> [!NOTE]
> <span data-ttu-id="89ca4-108">Para o fuso horário que não estão definido no registro, você pode criar fusos horários personalizados chamando as sobrecargas do <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método.</span><span class="sxs-lookup"><span data-stu-id="89ca4-108">For time zones that are not defined in the registry, you can create custom time zones by calling the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="89ca4-109">Criação de um fuso horário personalizado são discutidas no [como: criar fusos horários sem regras de ajuste](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) e [como: criar fusos horários com regras de ajuste](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) tópicos.</span><span class="sxs-lookup"><span data-stu-id="89ca4-109">Creating a custom time zone is discussed in the [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) topics.</span></span> <span data-ttu-id="89ca4-110">Além disso, você pode instanciar uma <xref:System.TimeZoneInfo> objeto restaurando-o de uma cadeia de caracteres serializada com o <xref:System.TimeZoneInfo.FromSerializedString%2A> método.</span><span class="sxs-lookup"><span data-stu-id="89ca4-110">In addition, you can instantiate a <xref:System.TimeZoneInfo> object by restoring it from a serialized string with the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span> <span data-ttu-id="89ca4-111">Serialização e desserialização de um <xref:System.TimeZoneInfo> objeto é abordado no [como: salvar fusos horários em um recurso incorporado](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) e [como: restaurar fusos horários de um recurso incorporado](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) tópicos.</span><span class="sxs-lookup"><span data-stu-id="89ca4-111">Serializing and deserializing a <xref:System.TimeZoneInfo> object is discussed in the [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) and [How to: Restore Time Zones from an Embedded Resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) topics.</span></span>

## <a name="accessing-individual-time-zones"></a><span data-ttu-id="89ca4-112">Acessando fusos horários individuais</span><span class="sxs-lookup"><span data-stu-id="89ca4-112">Accessing individual time zones</span></span>

<span data-ttu-id="89ca4-113">O <xref:System.TimeZoneInfo> classe fornece dois objetos de fuso horário predefinidos que representam a hora UTC e o fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="89ca4-113">The <xref:System.TimeZoneInfo> class provides two predefined time zone objects that represent the UTC time and the local time zone.</span></span> <span data-ttu-id="89ca4-114">Estão disponíveis no <xref:System.TimeZoneInfo.Utc%2A> e <xref:System.TimeZoneInfo.Local%2A> propriedades, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="89ca4-114">They are available from the <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A> properties, respectively.</span></span> <span data-ttu-id="89ca4-115">Para obter instruções sobre como acessar o UTC ou fusos horários locais, consulte [como: acessar os objetos de zona UTC e a hora local predefinidos](../../../docs/standard/datetime/access-utc-and-local.md).</span><span class="sxs-lookup"><span data-stu-id="89ca4-115">For instructions on accessing the UTC or local time zones, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md).</span></span>

<span data-ttu-id="89ca4-116">Você também pode instanciar uma <xref:System.TimeZoneInfo> objeto que representa qualquer fuso horário definido no registro.</span><span class="sxs-lookup"><span data-stu-id="89ca4-116">You can also instantiate a <xref:System.TimeZoneInfo> object that represents any time zone defined in the registry.</span></span> <span data-ttu-id="89ca4-117">Para obter instruções sobre como instanciar um objeto de fuso horário específico, consulte [como: instanciar um objeto TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span><span class="sxs-lookup"><span data-stu-id="89ca4-117">For instructions on instantiating a specific time zone object, see [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

## <a name="time-zone-identifiers"></a><span data-ttu-id="89ca4-118">Identificadores de fuso horário</span><span class="sxs-lookup"><span data-stu-id="89ca4-118">Time zone identifiers</span></span>

<span data-ttu-id="89ca4-119">O identificador do fuso horário é um campo de chave que identifica exclusivamente o fuso horário.</span><span class="sxs-lookup"><span data-stu-id="89ca4-119">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="89ca4-120">Enquanto a maioria das chaves são relativamente curtas, o identificador de fuso horário é comparativamente longo.</span><span class="sxs-lookup"><span data-stu-id="89ca4-120">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="89ca4-121">Na maioria dos casos, seu valor corresponde do <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> propriedade, que é usada para fornecer o nome do padrão de tempo do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="89ca4-121">In most cases, its value corresponds to the <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> property, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="89ca4-122">No entanto, há exceções.</span><span class="sxs-lookup"><span data-stu-id="89ca4-122">However, there are exceptions.</span></span> <span data-ttu-id="89ca4-123">A melhor maneira de certificar-se de que você forneça um identificador válido é enumerar os fusos horários disponíveis no sistema e observar os identificadores associados.</span><span class="sxs-lookup"><span data-stu-id="89ca4-123">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note their associated identifiers.</span></span>

## <a name="see-also"></a><span data-ttu-id="89ca4-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89ca4-124">See also</span></span>

<span data-ttu-id="89ca4-125">[Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
[como: acessar os objetos de zona UTC e a hora local predefinidos](../../../docs/standard/datetime/access-utc-and-local.md)
[como: instanciar um objeto TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) 
 [Convertendo horários entre fusos horários](../../../docs/standard/datetime/converting-between-time-zones.md)</span><span class="sxs-lookup"><span data-stu-id="89ca4-125">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md)
[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md)
[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md)</span></span>
