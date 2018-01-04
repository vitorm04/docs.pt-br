---
title: 224 - MessageThrottleAtSeventyPercent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e7d35407fe22dc913f7122163006035717d60d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="224---messagethrottleatseventypercent"></a><span data-ttu-id="d921c-102">224 - MessageThrottleAtSeventyPercent</span><span class="sxs-lookup"><span data-stu-id="d921c-102">224 - MessageThrottleAtSeventyPercent</span></span>
## <a name="properties"></a><span data-ttu-id="d921c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d921c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d921c-104">ID</span><span class="sxs-lookup"><span data-stu-id="d921c-104">ID</span></span>|<span data-ttu-id="d921c-105">224</span><span class="sxs-lookup"><span data-stu-id="d921c-105">224</span></span>|  
|<span data-ttu-id="d921c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="d921c-106">Keywords</span></span>|<span data-ttu-id="d921c-107">EndToEndMonitoring, HealthMonitoring, solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d921c-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="d921c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="d921c-108">Level</span></span>|<span data-ttu-id="d921c-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="d921c-109">Warning</span></span>|  
|<span data-ttu-id="d921c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d921c-110">Channel</span></span>|<span data-ttu-id="d921c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="d921c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d921c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d921c-112">Description</span></span>  
 <span data-ttu-id="d921c-113">Quando um serviço principal limitadores foi excedido, o `MessageThrottleExceeded` evento é emitido.</span><span class="sxs-lookup"><span data-stu-id="d921c-113">When one of the main service throttles has been exceeded, the `MessageThrottleExceeded` event is emitted.</span></span> <span data-ttu-id="d921c-114">Quando reduz o pico de atividade e o valor atual de acelerador é de 70% do limite atual, em seguida, esse evento é emitido.</span><span class="sxs-lookup"><span data-stu-id="d921c-114">When the spike of activity slows and the current value of the throttle is at 70 percent of the current limit then this event is emitted.</span></span> <span data-ttu-id="d921c-115">Observe que esse evento só é emitido quando como a atividade é mais lento.</span><span class="sxs-lookup"><span data-stu-id="d921c-115">Note that this event is only emitted once as the activity is slowing.</span></span> <span data-ttu-id="d921c-116">Se o valor atual é posicionado na marca de 70 por cento, (por exemplo, 70,69,70,71,70,69), somente a primeira ocorrência de 70% resulta em um evento.</span><span class="sxs-lookup"><span data-stu-id="d921c-116">If the current value hovers at the 70 percent mark, (for example, 70,69,70,71,70,69), only the first occurrence of 70 percent results in an event.</span></span> <span data-ttu-id="d921c-117">Depois que esse evento é emitido, ocorrências futuras de exceder a limitação limitam resultados em um `MessageThrottleExceeded` eventos.</span><span class="sxs-lookup"><span data-stu-id="d921c-117">After this event is emitted, future occurrences of exceeding the throttle's limit result in a `MessageThrottleExceeded` event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d921c-118">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d921c-118">Message</span></span>  
 <span data-ttu-id="d921c-119">O limite de restrição '%1' de '%2' está em 70% %.</span><span class="sxs-lookup"><span data-stu-id="d921c-119">The '%1' throttle limit of '%2' is at 70%%.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d921c-120">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d921c-120">Details</span></span>  
  
|<span data-ttu-id="d921c-121">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="d921c-121">Data Item Name</span></span>|<span data-ttu-id="d921c-122">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="d921c-122">Data Item Type</span></span>|<span data-ttu-id="d921c-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="d921c-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d921c-124">Nome do acelerador</span><span class="sxs-lookup"><span data-stu-id="d921c-124">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="d921c-125">O nome do acelerador foi excedido.</span><span class="sxs-lookup"><span data-stu-id="d921c-125">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="d921c-126">O `MaxConcurrentCalls`, `MaxConcurrentInstances`, ou `MaxConcurrentSessions`,</span><span class="sxs-lookup"><span data-stu-id="d921c-126">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="d921c-127">Limite</span><span class="sxs-lookup"><span data-stu-id="d921c-127">Limit</span></span>|`xs:long`|<span data-ttu-id="d921c-128">O limite configurado no momento do acelerador.</span><span class="sxs-lookup"><span data-stu-id="d921c-128">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="d921c-129">HostReference</span><span class="sxs-lookup"><span data-stu-id="d921c-129">HostReference</span></span>|`xs:string`|<span data-ttu-id="d921c-130">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="d921c-130">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d921c-131">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="d921c-131">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d921c-132">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="d921c-132">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d921c-133">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d921c-133">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d921c-134">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d921c-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
