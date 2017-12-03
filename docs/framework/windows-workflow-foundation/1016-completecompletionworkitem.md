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
ms.openlocfilehash: b01706f6e84987ea20f52c131139e243e8184c51
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="e4446-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="e4446-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e4446-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e4446-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e4446-104">ID</span><span class="sxs-lookup"><span data-stu-id="e4446-104">ID</span></span>|<span data-ttu-id="e4446-105">1016</span><span class="sxs-lookup"><span data-stu-id="e4446-105">1016</span></span>|  
|<span data-ttu-id="e4446-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="e4446-106">Keywords</span></span>|<span data-ttu-id="e4446-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e4446-107">WFRuntime</span></span>|  
|<span data-ttu-id="e4446-108">Nível</span><span class="sxs-lookup"><span data-stu-id="e4446-108">Level</span></span>|<span data-ttu-id="e4446-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="e4446-109">Verbose</span></span>|  
|<span data-ttu-id="e4446-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e4446-110">Channel</span></span>|<span data-ttu-id="e4446-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="e4446-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e4446-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4446-112">Description</span></span>  
 <span data-ttu-id="e4446-113">Indica que um CompletionWorkItem terminado.</span><span class="sxs-lookup"><span data-stu-id="e4446-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e4446-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="e4446-114">Message</span></span>  
 <span data-ttu-id="e4446-115">Um CompletionWorkItem concluiu para atividades pai “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="e4446-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="e4446-116">Atividade counting “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="e4446-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e4446-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e4446-117">Details</span></span>  
  
|<span data-ttu-id="e4446-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="e4446-118">Data Item Name</span></span>|<span data-ttu-id="e4446-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="e4446-119">Data Item Type</span></span>|<span data-ttu-id="e4446-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4446-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e4446-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="e4446-121">ParentActivity</span></span>|<span data-ttu-id="e4446-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4446-122">xs:string</span></span>|<span data-ttu-id="e4446-123">O nome do tipo de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="e4446-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="e4446-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="e4446-124">ParentDisplayName</span></span>|<span data-ttu-id="e4446-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4446-125">xs:string</span></span>|<span data-ttu-id="e4446-126">O nome para exibição de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="e4446-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="e4446-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="e4446-127">ParentInstanceId</span></span>|<span data-ttu-id="e4446-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4446-128">xs:string</span></span>|<span data-ttu-id="e4446-129">A identificação de instância de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="e4446-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="e4446-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="e4446-130">CompletedActivity</span></span>|<span data-ttu-id="e4446-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4446-131">xs:string</span></span>|<span data-ttu-id="e4446-132">O nome do tipo de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="e4446-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="e4446-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e4446-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="e4446-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4446-134">xs:string</span></span>|<span data-ttu-id="e4446-135">O nome para exibição de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="e4446-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="e4446-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e4446-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="e4446-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4446-137">xs:string</span></span>|<span data-ttu-id="e4446-138">A identificação de instância de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="e4446-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="e4446-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e4446-139">AppDomain</span></span>|<span data-ttu-id="e4446-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4446-140">xs:string</span></span>|<span data-ttu-id="e4446-141">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e4446-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
