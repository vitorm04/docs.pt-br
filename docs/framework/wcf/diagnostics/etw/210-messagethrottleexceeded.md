---
title: 210 - MessageThrottleExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c39c454e3a9bb70840b47271432d555d24fb167a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="210---messagethrottleexceeded"></a><span data-ttu-id="30643-102">210 - MessageThrottleExceeded</span><span class="sxs-lookup"><span data-stu-id="30643-102">210 - MessageThrottleExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="30643-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="30643-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="30643-104">ID</span><span class="sxs-lookup"><span data-stu-id="30643-104">ID</span></span>|<span data-ttu-id="30643-105">210</span><span class="sxs-lookup"><span data-stu-id="30643-105">210</span></span>|  
|<span data-ttu-id="30643-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="30643-106">Keywords</span></span>|<span data-ttu-id="30643-107">EndToEndMonitoring, HealthMonitoring, solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="30643-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="30643-108">Nível</span><span class="sxs-lookup"><span data-stu-id="30643-108">Level</span></span>|<span data-ttu-id="30643-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="30643-109">Warning</span></span>|  
|<span data-ttu-id="30643-110">Canal</span><span class="sxs-lookup"><span data-stu-id="30643-110">Channel</span></span>|<span data-ttu-id="30643-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="30643-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="30643-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="30643-112">Description</span></span>  
 <span data-ttu-id="30643-113">Esse evento é emitido quando um do serviço principal três limitadores tem sido excedidos.</span><span class="sxs-lookup"><span data-stu-id="30643-113">This event is emitted when one of the three main service throttles have been exceeded.</span></span> <span data-ttu-id="30643-114">Observe que esse evento só é emitido quando o limite for excedido inicialmente.</span><span class="sxs-lookup"><span data-stu-id="30643-114">Note that this event is only emitted when the throttle limit is initially exceeded.</span></span> <span data-ttu-id="30643-115">Por exemplo, se o limite de chamadas simultâneas for 10, a simultâneas 11 resultados da chamada um `MessageThrottleExceeded` eventos.</span><span class="sxs-lookup"><span data-stu-id="30643-115">For example, if the throttle limit for concurrent calls is 10, the 11th concurrent call results in a `MessageThrottleExceeded` event.</span></span> <span data-ttu-id="30643-116">12 de chamada não resulta em outro evento.</span><span class="sxs-lookup"><span data-stu-id="30643-116">The 12th call does not result in another event.</span></span> <span data-ttu-id="30643-117">Além disso, para evitar um fluxo de eventos com ruídos, atividade que passa em torno de limite não resulta em outro evento.</span><span class="sxs-lookup"><span data-stu-id="30643-117">Additionally, to avoid a noisy event stream, activity that hovers around the limit does not result in another event.</span></span> <span data-ttu-id="30643-118">Neste exemplo, se duas chamadas concluída, em seguida, há 9 chamadas simultâneas.</span><span class="sxs-lookup"><span data-stu-id="30643-118">In this example, if a couple of calls complete then there are 9 concurrent calls.</span></span> <span data-ttu-id="30643-119">Se subsequentemente duas chamadas mais entrar, o valor atual é 11 novamente.</span><span class="sxs-lookup"><span data-stu-id="30643-119">If subsequently two more calls come in, the current value is again 11.</span></span> <span data-ttu-id="30643-120">Não, isso resulta em outro evento.</span><span class="sxs-lookup"><span data-stu-id="30643-120">This does not result in another event.</span></span> <span data-ttu-id="30643-121">Quando o valor atual a 70 por cento do limite de limitação de um evento diferente é emitido que indica que a atividade tem parou.</span><span class="sxs-lookup"><span data-stu-id="30643-121">When the current value falls to 70 percent of the throttle limit a different event is emitted that indicates that the activity has slowed.</span></span> <span data-ttu-id="30643-122">Atividades futuras que excedem o limite de resultados em outra `MessageThrottleExceeded` evento que está sendo emitido.</span><span class="sxs-lookup"><span data-stu-id="30643-122">Future activity that exceeds the limit results in another `MessageThrottleExceeded` event being emitted.</span></span> <span data-ttu-id="30643-123">Neste exemplo, se a quantidade de chamadas simultâneas fica 7 e, em seguida, novamente atinge 11 e outro `MessageThrottleExceeded` evento é emitido.</span><span class="sxs-lookup"><span data-stu-id="30643-123">In this example, if the amount of concurrent calls falls to 7 and then again reaches 11 and another `MessageThrottleExceeded` event is emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="30643-124">Mensagem</span><span class="sxs-lookup"><span data-stu-id="30643-124">Message</span></span>  
 <span data-ttu-id="30643-125">Foi atingido o limite de restrição '%1' de '%2'.</span><span class="sxs-lookup"><span data-stu-id="30643-125">The '%1' throttle limit of '%2' was hit.</span></span>  
  
## <a name="details"></a><span data-ttu-id="30643-126">Detalhes</span><span class="sxs-lookup"><span data-stu-id="30643-126">Details</span></span>  
  
|<span data-ttu-id="30643-127">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="30643-127">Data Item Name</span></span>|<span data-ttu-id="30643-128">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="30643-128">Data Item Type</span></span>|<span data-ttu-id="30643-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="30643-129">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="30643-130">Nome do acelerador</span><span class="sxs-lookup"><span data-stu-id="30643-130">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="30643-131">O nome do acelerador foi excedido.</span><span class="sxs-lookup"><span data-stu-id="30643-131">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="30643-132">O `MaxConcurrentCalls`, `MaxConcurrentInstances`, ou `MaxConcurrentSessions`,</span><span class="sxs-lookup"><span data-stu-id="30643-132">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="30643-133">Limite</span><span class="sxs-lookup"><span data-stu-id="30643-133">Limit</span></span>|`xs:long`|<span data-ttu-id="30643-134">O limite configurado no momento do acelerador.</span><span class="sxs-lookup"><span data-stu-id="30643-134">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="30643-135">HostReference</span><span class="sxs-lookup"><span data-stu-id="30643-135">HostReference</span></span>|`xs:string`|<span data-ttu-id="30643-136">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="30643-136">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="30643-137">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="30643-137">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="30643-138">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="30643-138">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="30643-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="30643-139">AppDomain</span></span>|`xs:string`|<span data-ttu-id="30643-140">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="30643-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
