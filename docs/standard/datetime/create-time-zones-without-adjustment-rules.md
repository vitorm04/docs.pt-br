---
title: 'Como: criar fusos horários sem regras de ajuste'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 214e3bca811f87f4b8367b459564449d16e7c289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572896"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="fcd19-102">Como: criar fusos horários sem regras de ajuste</span><span class="sxs-lookup"><span data-stu-id="fcd19-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="fcd19-103">As informações de fuso horário preciso exigidas por um aplicativo podem não estar presentes em um determinado sistema por vários motivos:</span><span class="sxs-lookup"><span data-stu-id="fcd19-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

* <span data-ttu-id="fcd19-104">O fuso horário nunca foi definido no registro do sistema local.</span><span class="sxs-lookup"><span data-stu-id="fcd19-104">The time zone has never been defined in the local system's registry.</span></span>

* <span data-ttu-id="fcd19-105">Dados sobre o fuso horário foi modificados ou removidos do registro.</span><span class="sxs-lookup"><span data-stu-id="fcd19-105">Data about the time zone has been modified or removed from the registry.</span></span>

* <span data-ttu-id="fcd19-106">O fuso horário existe mas não tem informações precisas sobre ajustes de fuso horário para um período específico do histórico.</span><span class="sxs-lookup"><span data-stu-id="fcd19-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="fcd19-107">Nesses casos, você pode chamar o <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método para definir o fuso horário exigido pelo seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fcd19-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="fcd19-108">Você pode usar as sobrecargas do método para criar um fuso horário com ou sem regras de ajuste.</span><span class="sxs-lookup"><span data-stu-id="fcd19-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="fcd19-109">Se o fuso horário dá suporte ao horário de verão, você pode definir ajustes com a regras de ajuste fixo ou flutuante.</span><span class="sxs-lookup"><span data-stu-id="fcd19-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="fcd19-110">(Para obter definições desses termos, consulte a seção "Terminologia de fuso horário" [visão geral de fuso horário](../../../docs/standard/datetime/time-zone-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="fcd19-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fcd19-111">Fusos horários personalizados criados ao chamar o <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método não são adicionados ao registro.</span><span class="sxs-lookup"><span data-stu-id="fcd19-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="fcd19-112">Em vez disso, eles podem ser acessados apenas pela referência de objeto retornada pelo <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> chamada de método.</span><span class="sxs-lookup"><span data-stu-id="fcd19-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="fcd19-113">Este tópico mostra como criar um fuso horário sem regras de ajuste.</span><span class="sxs-lookup"><span data-stu-id="fcd19-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="fcd19-114">Para criar um fuso horário que dá suporte a regras de ajuste de horário de verão, consulte [como: criar fusos horários com regras de ajuste](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="fcd19-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="fcd19-115">Para criar um fuso horário sem regras de ajuste</span><span class="sxs-lookup"><span data-stu-id="fcd19-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="fcd19-116">Defina nome para exibição do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fcd19-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="fcd19-117">O nome para exibição segue um formato razoavelmente padrão no qual o deslocamento do fuso horário do tempo Universal Coordenado (UTC) é colocado entre parênteses e é seguido por uma cadeia de caracteres que identifica o fuso horário, uma ou mais das cidades no fuso horário ou um ou mais do cou ntries ou regiões no fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fcd19-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="fcd19-118">Defina o nome do padrão de tempo do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fcd19-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="fcd19-119">Normalmente, essa cadeia de caracteres também é usada como identificador do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fcd19-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="fcd19-120">Se você quiser usar um identificador diferente do nome padrão do fuso horário, defina o identificador de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fcd19-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="fcd19-121">Criar uma instância de um <xref:System.TimeSpan> objeto que define o deslocamento do fuso horário do UTC.</span><span class="sxs-lookup"><span data-stu-id="fcd19-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="fcd19-122">Fusos horários com horários posteriores ao UTC têm um deslocamento positivo.</span><span class="sxs-lookup"><span data-stu-id="fcd19-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="fcd19-123">Fusos horários com horários anteriores ao UTC têm um deslocamento negativo.</span><span class="sxs-lookup"><span data-stu-id="fcd19-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="fcd19-124">Chamar o <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> método para instanciar o novo fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fcd19-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="fcd19-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fcd19-125">Example</span></span>

<span data-ttu-id="fcd19-126">O exemplo a seguir define um fuso horário personalizado para Mawson, Antártida, que não tem nenhuma regra de ajuste.</span><span class="sxs-lookup"><span data-stu-id="fcd19-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="fcd19-127">A cadeia de caracteres atribuída para o <xref:System.TimeZoneInfo.DisplayName%2A> propriedade segue um formato padrão no qual o deslocamento do fuso horário do UTC é seguido por uma descrição amigável do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fcd19-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="fcd19-128">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="fcd19-128">Compiling the code</span></span>

<span data-ttu-id="fcd19-129">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="fcd19-129">This example requires:</span></span>

* <span data-ttu-id="fcd19-130">Que uma referência a System.Core.dll seja adicionada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="fcd19-130">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="fcd19-131">Se os namespaces a seguir sejam importados:</span><span class="sxs-lookup"><span data-stu-id="fcd19-131">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="fcd19-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcd19-132">See also</span></span>

<span data-ttu-id="fcd19-133">[Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
[visão geral de fuso horário](../../../docs/standard/datetime/time-zone-overview.md)
[como: criar fusos horários com regras de ajuste](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)</span><span class="sxs-lookup"><span data-stu-id="fcd19-133">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)</span></span>
