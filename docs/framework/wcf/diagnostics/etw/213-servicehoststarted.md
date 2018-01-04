---
title: 213 - ServiceHostStarted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a83cb1cfb87b562add1a791de5a651b563d63d4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="91629-102">213 - ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="91629-102">213 - ServiceHostStarted</span></span>
## <a name="properties"></a><span data-ttu-id="91629-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="91629-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="91629-104">ID</span><span class="sxs-lookup"><span data-stu-id="91629-104">ID</span></span>|<span data-ttu-id="91629-105">213</span><span class="sxs-lookup"><span data-stu-id="91629-105">213</span></span>|  
|<span data-ttu-id="91629-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="91629-106">Keywords</span></span>|<span data-ttu-id="91629-107">EndToEndMonitoring, HealthMonitoring, solução de problemas, ServiceHost</span><span class="sxs-lookup"><span data-stu-id="91629-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="91629-108">Nível</span><span class="sxs-lookup"><span data-stu-id="91629-108">Level</span></span>|<span data-ttu-id="91629-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="91629-109">LogAlways</span></span>|  
|<span data-ttu-id="91629-110">Canal</span><span class="sxs-lookup"><span data-stu-id="91629-110">Channel</span></span>|<span data-ttu-id="91629-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="91629-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="91629-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="91629-112">Description</span></span>  
 <span data-ttu-id="91629-113">Esse evento é emitido quando um host de serviço hospedado da Web é iniciado.</span><span class="sxs-lookup"><span data-stu-id="91629-113">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="91629-114">Isso geralmente acontece quando o serviço está ativado por uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="91629-114">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="91629-115">Ele também pode ocorrer se o serviço está configurado para ser iniciado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="91629-115">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="91629-116">Mensagem</span><span class="sxs-lookup"><span data-stu-id="91629-116">Message</span></span>  
 <span data-ttu-id="91629-117">ServiceHost iniciado: '%1'.</span><span class="sxs-lookup"><span data-stu-id="91629-117">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="91629-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="91629-118">Details</span></span>  
  
|<span data-ttu-id="91629-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="91629-119">Data Item Name</span></span>|<span data-ttu-id="91629-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="91629-120">Data Item Type</span></span>|<span data-ttu-id="91629-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="91629-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="91629-122">Nome do tipo de serviço</span><span class="sxs-lookup"><span data-stu-id="91629-122">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="91629-123">O FullName do CLR do tipo de implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="91629-123">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="91629-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="91629-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="91629-125">Os serviços hospedados da Web, este campo identificam exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="91629-125">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="91629-126">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="91629-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="91629-127">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="91629-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="91629-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="91629-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="91629-129">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="91629-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
