---
title: 1015 - StartCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc317157ed7658a52aa60c9b74942f9e84d47257
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="c477e-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="c477e-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c477e-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c477e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c477e-104">ID</span><span class="sxs-lookup"><span data-stu-id="c477e-104">ID</span></span>|<span data-ttu-id="c477e-105">1015</span><span class="sxs-lookup"><span data-stu-id="c477e-105">1015</span></span>|  
|<span data-ttu-id="c477e-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="c477e-106">Keywords</span></span>|<span data-ttu-id="c477e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c477e-107">WFRuntime</span></span>|  
|<span data-ttu-id="c477e-108">Nível</span><span class="sxs-lookup"><span data-stu-id="c477e-108">Level</span></span>|<span data-ttu-id="c477e-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="c477e-109">Verbose</span></span>|  
|<span data-ttu-id="c477e-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c477e-110">Channel</span></span>|<span data-ttu-id="c477e-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="c477e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c477e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c477e-112">Description</span></span>  
 <span data-ttu-id="c477e-113">Indica que um CompletionWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="c477e-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c477e-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c477e-114">Message</span></span>  
 <span data-ttu-id="c477e-115">Iniciar a execução de um CompletionWorkItem para atividades pai “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="c477e-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="c477e-116">Atividade counting “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="c477e-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c477e-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c477e-117">Details</span></span>  
  
|<span data-ttu-id="c477e-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="c477e-118">Data Item Name</span></span>|<span data-ttu-id="c477e-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="c477e-119">Data Item Type</span></span>|<span data-ttu-id="c477e-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="c477e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c477e-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="c477e-121">ParentActivity</span></span>|<span data-ttu-id="c477e-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="c477e-122">xs:string</span></span>|<span data-ttu-id="c477e-123">O nome do tipo de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="c477e-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="c477e-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="c477e-124">ParentDisplayName</span></span>|<span data-ttu-id="c477e-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="c477e-125">xs:string</span></span>|<span data-ttu-id="c477e-126">O nome para exibição de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="c477e-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="c477e-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="c477e-127">ParentInstanceId</span></span>|<span data-ttu-id="c477e-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="c477e-128">xs:string</span></span>|<span data-ttu-id="c477e-129">A identificação de instância de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="c477e-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="c477e-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="c477e-130">CompletedActivity</span></span>|<span data-ttu-id="c477e-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="c477e-131">xs:string</span></span>|<span data-ttu-id="c477e-132">O nome do tipo de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="c477e-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="c477e-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="c477e-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="c477e-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="c477e-134">xs:string</span></span>|<span data-ttu-id="c477e-135">O nome para exibição de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="c477e-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="c477e-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="c477e-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="c477e-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="c477e-137">xs:string</span></span>|<span data-ttu-id="c477e-138">A identificação de instância de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="c477e-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="c477e-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c477e-139">AppDomain</span></span>|<span data-ttu-id="c477e-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="c477e-140">xs:string</span></span>|<span data-ttu-id="c477e-141">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c477e-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
