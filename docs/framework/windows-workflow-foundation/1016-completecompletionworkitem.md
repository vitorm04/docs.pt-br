---
title: 1016 - CompleteCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f9b09001212de6d5aa4f5fde577b9eeb9d967ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="b10bb-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="b10bb-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="b10bb-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b10bb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b10bb-104">ID</span><span class="sxs-lookup"><span data-stu-id="b10bb-104">ID</span></span>|<span data-ttu-id="b10bb-105">1016</span><span class="sxs-lookup"><span data-stu-id="b10bb-105">1016</span></span>|  
|<span data-ttu-id="b10bb-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="b10bb-106">Keywords</span></span>|<span data-ttu-id="b10bb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b10bb-107">WFRuntime</span></span>|  
|<span data-ttu-id="b10bb-108">Nível</span><span class="sxs-lookup"><span data-stu-id="b10bb-108">Level</span></span>|<span data-ttu-id="b10bb-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="b10bb-109">Verbose</span></span>|  
|<span data-ttu-id="b10bb-110">Canal</span><span class="sxs-lookup"><span data-stu-id="b10bb-110">Channel</span></span>|<span data-ttu-id="b10bb-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="b10bb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b10bb-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b10bb-112">Description</span></span>  
 <span data-ttu-id="b10bb-113">Indica que um CompletionWorkItem terminado.</span><span class="sxs-lookup"><span data-stu-id="b10bb-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b10bb-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="b10bb-114">Message</span></span>  
 <span data-ttu-id="b10bb-115">Um CompletionWorkItem concluiu para atividades pai “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="b10bb-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="b10bb-116">Atividade counting “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="b10bb-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b10bb-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="b10bb-117">Details</span></span>  
  
|<span data-ttu-id="b10bb-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="b10bb-118">Data Item Name</span></span>|<span data-ttu-id="b10bb-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="b10bb-119">Data Item Type</span></span>|<span data-ttu-id="b10bb-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="b10bb-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b10bb-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="b10bb-121">ParentActivity</span></span>|<span data-ttu-id="b10bb-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="b10bb-122">xs:string</span></span>|<span data-ttu-id="b10bb-123">O nome do tipo de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="b10bb-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="b10bb-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="b10bb-124">ParentDisplayName</span></span>|<span data-ttu-id="b10bb-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="b10bb-125">xs:string</span></span>|<span data-ttu-id="b10bb-126">O nome para exibição de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="b10bb-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="b10bb-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="b10bb-127">ParentInstanceId</span></span>|<span data-ttu-id="b10bb-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="b10bb-128">xs:string</span></span>|<span data-ttu-id="b10bb-129">A identificação de instância de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="b10bb-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="b10bb-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="b10bb-130">CompletedActivity</span></span>|<span data-ttu-id="b10bb-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="b10bb-131">xs:string</span></span>|<span data-ttu-id="b10bb-132">O nome do tipo de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="b10bb-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="b10bb-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="b10bb-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="b10bb-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="b10bb-134">xs:string</span></span>|<span data-ttu-id="b10bb-135">O nome para exibição de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="b10bb-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="b10bb-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="b10bb-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="b10bb-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="b10bb-137">xs:string</span></span>|<span data-ttu-id="b10bb-138">A identificação de instância de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="b10bb-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="b10bb-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b10bb-139">AppDomain</span></span>|<span data-ttu-id="b10bb-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="b10bb-140">xs:string</span></span>|<span data-ttu-id="b10bb-141">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b10bb-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
