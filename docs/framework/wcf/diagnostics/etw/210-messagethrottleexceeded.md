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
ms.workload: dotnet
ms.openlocfilehash: 299cc11dc4f6794b65761ad7da71bcf062c318db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="210---messagethrottleexceeded"></a><span data-ttu-id="f4d81-102">210 - MessageThrottleExceeded</span><span class="sxs-lookup"><span data-stu-id="f4d81-102">210 - MessageThrottleExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="f4d81-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f4d81-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4d81-104">ID</span><span class="sxs-lookup"><span data-stu-id="f4d81-104">ID</span></span>|<span data-ttu-id="f4d81-105">210</span><span class="sxs-lookup"><span data-stu-id="f4d81-105">210</span></span>|  
|<span data-ttu-id="f4d81-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="f4d81-106">Keywords</span></span>|<span data-ttu-id="f4d81-107">EndToEndMonitoring, HealthMonitoring, solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f4d81-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f4d81-108">Nível</span><span class="sxs-lookup"><span data-stu-id="f4d81-108">Level</span></span>|<span data-ttu-id="f4d81-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="f4d81-109">Warning</span></span>|  
|<span data-ttu-id="f4d81-110">Canal</span><span class="sxs-lookup"><span data-stu-id="f4d81-110">Channel</span></span>|<span data-ttu-id="f4d81-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="f4d81-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f4d81-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4d81-112">Description</span></span>  
 <span data-ttu-id="f4d81-113">Esse evento é emitido quando um do serviço principal três limitadores tem sido excedidos.</span><span class="sxs-lookup"><span data-stu-id="f4d81-113">This event is emitted when one of the three main service throttles have been exceeded.</span></span> <span data-ttu-id="f4d81-114">Observe que esse evento só é emitido quando o limite for excedido inicialmente.</span><span class="sxs-lookup"><span data-stu-id="f4d81-114">Note that this event is only emitted when the throttle limit is initially exceeded.</span></span> <span data-ttu-id="f4d81-115">Por exemplo, se o limite de chamadas simultâneas for 10, a simultâneas 11 resultados da chamada um `MessageThrottleExceeded` eventos.</span><span class="sxs-lookup"><span data-stu-id="f4d81-115">For example, if the throttle limit for concurrent calls is 10, the 11th concurrent call results in a `MessageThrottleExceeded` event.</span></span> <span data-ttu-id="f4d81-116">12 de chamada não resulta em outro evento.</span><span class="sxs-lookup"><span data-stu-id="f4d81-116">The 12th call does not result in another event.</span></span> <span data-ttu-id="f4d81-117">Além disso, para evitar um fluxo de eventos com ruídos, atividade que passa em torno de limite não resulta em outro evento.</span><span class="sxs-lookup"><span data-stu-id="f4d81-117">Additionally, to avoid a noisy event stream, activity that hovers around the limit does not result in another event.</span></span> <span data-ttu-id="f4d81-118">Neste exemplo, se duas chamadas concluída, em seguida, há 9 chamadas simultâneas.</span><span class="sxs-lookup"><span data-stu-id="f4d81-118">In this example, if a couple of calls complete then there are 9 concurrent calls.</span></span> <span data-ttu-id="f4d81-119">Se subsequentemente duas chamadas mais entrar, o valor atual é 11 novamente.</span><span class="sxs-lookup"><span data-stu-id="f4d81-119">If subsequently two more calls come in, the current value is again 11.</span></span> <span data-ttu-id="f4d81-120">Não, isso resulta em outro evento.</span><span class="sxs-lookup"><span data-stu-id="f4d81-120">This does not result in another event.</span></span> <span data-ttu-id="f4d81-121">Quando o valor atual a 70 por cento do limite de limitação de um evento diferente é emitido que indica que a atividade tem parou.</span><span class="sxs-lookup"><span data-stu-id="f4d81-121">When the current value falls to 70 percent of the throttle limit a different event is emitted that indicates that the activity has slowed.</span></span> <span data-ttu-id="f4d81-122">Atividades futuras que excedem o limite de resultados em outra `MessageThrottleExceeded` evento que está sendo emitido.</span><span class="sxs-lookup"><span data-stu-id="f4d81-122">Future activity that exceeds the limit results in another `MessageThrottleExceeded` event being emitted.</span></span> <span data-ttu-id="f4d81-123">Neste exemplo, se a quantidade de chamadas simultâneas fica 7 e, em seguida, novamente atinge 11 e outro `MessageThrottleExceeded` evento é emitido.</span><span class="sxs-lookup"><span data-stu-id="f4d81-123">In this example, if the amount of concurrent calls falls to 7 and then again reaches 11 and another `MessageThrottleExceeded` event is emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f4d81-124">Mensagem</span><span class="sxs-lookup"><span data-stu-id="f4d81-124">Message</span></span>  
 <span data-ttu-id="f4d81-125">Foi atingido o limite de restrição '%1' de '%2'.</span><span class="sxs-lookup"><span data-stu-id="f4d81-125">The '%1' throttle limit of '%2' was hit.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f4d81-126">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f4d81-126">Details</span></span>  
  
|<span data-ttu-id="f4d81-127">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="f4d81-127">Data Item Name</span></span>|<span data-ttu-id="f4d81-128">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="f4d81-128">Data Item Type</span></span>|<span data-ttu-id="f4d81-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4d81-129">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f4d81-130">Nome do acelerador</span><span class="sxs-lookup"><span data-stu-id="f4d81-130">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="f4d81-131">O nome do acelerador foi excedido.</span><span class="sxs-lookup"><span data-stu-id="f4d81-131">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="f4d81-132">O `MaxConcurrentCalls`, `MaxConcurrentInstances`, ou `MaxConcurrentSessions`,</span><span class="sxs-lookup"><span data-stu-id="f4d81-132">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="f4d81-133">Limite</span><span class="sxs-lookup"><span data-stu-id="f4d81-133">Limit</span></span>|`xs:long`|<span data-ttu-id="f4d81-134">O limite configurado no momento do acelerador.</span><span class="sxs-lookup"><span data-stu-id="f4d81-134">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="f4d81-135">HostReference</span><span class="sxs-lookup"><span data-stu-id="f4d81-135">HostReference</span></span>|`xs:string`|<span data-ttu-id="f4d81-136">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="f4d81-136">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f4d81-137">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="f4d81-137">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f4d81-138">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="f4d81-138">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f4d81-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f4d81-139">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f4d81-140">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f4d81-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
