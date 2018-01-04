---
title: 57398 - MaxInstancesExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba48f19de1be3cfd2461e159b91fa365e24ee750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="56eee-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="56eee-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="56eee-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="56eee-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="56eee-104">ID</span><span class="sxs-lookup"><span data-stu-id="56eee-104">ID</span></span>|<span data-ttu-id="56eee-105">57398</span><span class="sxs-lookup"><span data-stu-id="56eee-105">57398</span></span>|  
|<span data-ttu-id="56eee-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="56eee-106">Keywords</span></span>|<span data-ttu-id="56eee-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="56eee-107">WFServices</span></span>|  
|<span data-ttu-id="56eee-108">Nível</span><span class="sxs-lookup"><span data-stu-id="56eee-108">Level</span></span>|<span data-ttu-id="56eee-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="56eee-109">Warning</span></span>|  
|<span data-ttu-id="56eee-110">Canal</span><span class="sxs-lookup"><span data-stu-id="56eee-110">Channel</span></span>|<span data-ttu-id="56eee-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="56eee-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="56eee-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="56eee-112">Description</span></span>  
 <span data-ttu-id="56eee-113">Indica que o sistema/o limite definido para o regulador de pressão “MaxConcurrentInstances”.</span><span class="sxs-lookup"><span data-stu-id="56eee-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="56eee-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="56eee-114">Message</span></span>  
 <span data-ttu-id="56eee-115">O sistema atingiu o limite definido para o acelerador 'MaxConcurrentInstances'.</span><span class="sxs-lookup"><span data-stu-id="56eee-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="56eee-116">O limite para este regulador de pressão foi definido como %1.</span><span class="sxs-lookup"><span data-stu-id="56eee-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="56eee-117">O valor do acelerador pode ser alterado pela modificação do atributo 'maxConcurrentInstances' no elemento serviceThrottle ou modificando-se a propriedade 'MaxConcurrentInstances' no comportamento ServiceThrottlingBehavior.</span><span class="sxs-lookup"><span data-stu-id="56eee-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="56eee-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="56eee-118">Details</span></span>  
  
|<span data-ttu-id="56eee-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="56eee-119">Data Item Name</span></span>|<span data-ttu-id="56eee-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="56eee-120">Data Item Type</span></span>|<span data-ttu-id="56eee-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="56eee-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="56eee-122">Nome</span><span class="sxs-lookup"><span data-stu-id="56eee-122">Name</span></span>|<span data-ttu-id="56eee-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="56eee-123">xs:string</span></span>|<span data-ttu-id="56eee-124">O nome do item.</span><span class="sxs-lookup"><span data-stu-id="56eee-124">The name of the item.</span></span>|  
|<span data-ttu-id="56eee-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="56eee-125">AppDomain</span></span>|<span data-ttu-id="56eee-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="56eee-126">xs:string</span></span>|<span data-ttu-id="56eee-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="56eee-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
