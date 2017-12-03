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
ms.openlocfilehash: 803616fdd287491afa27d3ac23dfce99c5db08ca
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="cac50-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="cac50-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="cac50-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="cac50-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cac50-104">ID</span><span class="sxs-lookup"><span data-stu-id="cac50-104">ID</span></span>|<span data-ttu-id="cac50-105">57398</span><span class="sxs-lookup"><span data-stu-id="cac50-105">57398</span></span>|  
|<span data-ttu-id="cac50-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="cac50-106">Keywords</span></span>|<span data-ttu-id="cac50-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="cac50-107">WFServices</span></span>|  
|<span data-ttu-id="cac50-108">Nível</span><span class="sxs-lookup"><span data-stu-id="cac50-108">Level</span></span>|<span data-ttu-id="cac50-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="cac50-109">Warning</span></span>|  
|<span data-ttu-id="cac50-110">Canal</span><span class="sxs-lookup"><span data-stu-id="cac50-110">Channel</span></span>|<span data-ttu-id="cac50-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="cac50-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cac50-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="cac50-112">Description</span></span>  
 <span data-ttu-id="cac50-113">Indica que o sistema/o limite definido para o regulador de pressão “MaxConcurrentInstances”.</span><span class="sxs-lookup"><span data-stu-id="cac50-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cac50-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="cac50-114">Message</span></span>  
 <span data-ttu-id="cac50-115">O sistema atingiu o limite definido para o acelerador 'MaxConcurrentInstances'.</span><span class="sxs-lookup"><span data-stu-id="cac50-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="cac50-116">O limite para este regulador de pressão foi definido como %1.</span><span class="sxs-lookup"><span data-stu-id="cac50-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="cac50-117">O valor do acelerador pode ser alterado pela modificação do atributo 'maxConcurrentInstances' no elemento serviceThrottle ou modificando-se a propriedade 'MaxConcurrentInstances' no comportamento ServiceThrottlingBehavior.</span><span class="sxs-lookup"><span data-stu-id="cac50-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cac50-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="cac50-118">Details</span></span>  
  
|<span data-ttu-id="cac50-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="cac50-119">Data Item Name</span></span>|<span data-ttu-id="cac50-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="cac50-120">Data Item Type</span></span>|<span data-ttu-id="cac50-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="cac50-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cac50-122">Nome</span><span class="sxs-lookup"><span data-stu-id="cac50-122">Name</span></span>|<span data-ttu-id="cac50-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="cac50-123">xs:string</span></span>|<span data-ttu-id="cac50-124">O nome do item.</span><span class="sxs-lookup"><span data-stu-id="cac50-124">The name of the item.</span></span>|  
|<span data-ttu-id="cac50-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cac50-125">AppDomain</span></span>|<span data-ttu-id="cac50-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="cac50-126">xs:string</span></span>|<span data-ttu-id="cac50-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="cac50-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
