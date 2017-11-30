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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a7c6b6060e8dd3256d23db7350299d2670f6caa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="73bf7-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="73bf7-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="73bf7-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="73bf7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="73bf7-104">ID</span><span class="sxs-lookup"><span data-stu-id="73bf7-104">ID</span></span>|<span data-ttu-id="73bf7-105">1016</span><span class="sxs-lookup"><span data-stu-id="73bf7-105">1016</span></span>|  
|<span data-ttu-id="73bf7-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="73bf7-106">Keywords</span></span>|<span data-ttu-id="73bf7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="73bf7-107">WFRuntime</span></span>|  
|<span data-ttu-id="73bf7-108">Nível</span><span class="sxs-lookup"><span data-stu-id="73bf7-108">Level</span></span>|<span data-ttu-id="73bf7-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="73bf7-109">Verbose</span></span>|  
|<span data-ttu-id="73bf7-110">Canal</span><span class="sxs-lookup"><span data-stu-id="73bf7-110">Channel</span></span>|<span data-ttu-id="73bf7-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="73bf7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="73bf7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="73bf7-112">Description</span></span>  
 <span data-ttu-id="73bf7-113">Indica que um CompletionWorkItem terminado.</span><span class="sxs-lookup"><span data-stu-id="73bf7-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="73bf7-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="73bf7-114">Message</span></span>  
 <span data-ttu-id="73bf7-115">Um CompletionWorkItem concluiu para atividades pai “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="73bf7-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="73bf7-116">Atividade counting “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="73bf7-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="73bf7-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="73bf7-117">Details</span></span>  
  
|<span data-ttu-id="73bf7-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="73bf7-118">Data Item Name</span></span>|<span data-ttu-id="73bf7-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="73bf7-119">Data Item Type</span></span>|<span data-ttu-id="73bf7-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="73bf7-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="73bf7-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="73bf7-121">ParentActivity</span></span>|<span data-ttu-id="73bf7-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="73bf7-122">xs:string</span></span>|<span data-ttu-id="73bf7-123">O nome do tipo de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="73bf7-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="73bf7-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="73bf7-124">ParentDisplayName</span></span>|<span data-ttu-id="73bf7-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="73bf7-125">xs:string</span></span>|<span data-ttu-id="73bf7-126">O nome para exibição de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="73bf7-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="73bf7-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="73bf7-127">ParentInstanceId</span></span>|<span data-ttu-id="73bf7-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="73bf7-128">xs:string</span></span>|<span data-ttu-id="73bf7-129">A identificação de instância de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="73bf7-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="73bf7-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="73bf7-130">CompletedActivity</span></span>|<span data-ttu-id="73bf7-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="73bf7-131">xs:string</span></span>|<span data-ttu-id="73bf7-132">O nome do tipo de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="73bf7-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="73bf7-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="73bf7-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="73bf7-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="73bf7-134">xs:string</span></span>|<span data-ttu-id="73bf7-135">O nome para exibição de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="73bf7-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="73bf7-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="73bf7-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="73bf7-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="73bf7-137">xs:string</span></span>|<span data-ttu-id="73bf7-138">A identificação de instância de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="73bf7-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="73bf7-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="73bf7-139">AppDomain</span></span>|<span data-ttu-id="73bf7-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="73bf7-140">xs:string</span></span>|<span data-ttu-id="73bf7-141">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="73bf7-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
