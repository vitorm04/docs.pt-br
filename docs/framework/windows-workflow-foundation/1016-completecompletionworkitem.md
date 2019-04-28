---
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 3f0904a561a242cd3be528c9707a409b6f98e0fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925080"
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="6d3e4-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="6d3e4-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="6d3e4-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="6d3e4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6d3e4-104">ID</span><span class="sxs-lookup"><span data-stu-id="6d3e4-104">ID</span></span>|<span data-ttu-id="6d3e4-105">1016</span><span class="sxs-lookup"><span data-stu-id="6d3e4-105">1016</span></span>|  
|<span data-ttu-id="6d3e4-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="6d3e4-106">Keywords</span></span>|<span data-ttu-id="6d3e4-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6d3e4-107">WFRuntime</span></span>|  
|<span data-ttu-id="6d3e4-108">Nível</span><span class="sxs-lookup"><span data-stu-id="6d3e4-108">Level</span></span>|<span data-ttu-id="6d3e4-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="6d3e4-109">Verbose</span></span>|  
|<span data-ttu-id="6d3e4-110">Canal</span><span class="sxs-lookup"><span data-stu-id="6d3e4-110">Channel</span></span>|<span data-ttu-id="6d3e4-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="6d3e4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6d3e4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d3e4-112">Description</span></span>  
 <span data-ttu-id="6d3e4-113">Indica que um CompletionWorkItem terminado.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6d3e4-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="6d3e4-114">Message</span></span>  
 <span data-ttu-id="6d3e4-115">Um CompletionWorkItem concluiu para atividades pai “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="6d3e4-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="6d3e4-116">Atividade counting “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="6d3e4-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6d3e4-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="6d3e4-117">Details</span></span>  
  
|<span data-ttu-id="6d3e4-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="6d3e4-118">Data Item Name</span></span>|<span data-ttu-id="6d3e4-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="6d3e4-119">Data Item Type</span></span>|<span data-ttu-id="6d3e4-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d3e4-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6d3e4-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="6d3e4-121">ParentActivity</span></span>|<span data-ttu-id="6d3e4-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="6d3e4-122">xs:string</span></span>|<span data-ttu-id="6d3e4-123">O nome do tipo de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="6d3e4-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="6d3e4-124">ParentDisplayName</span></span>|<span data-ttu-id="6d3e4-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="6d3e4-125">xs:string</span></span>|<span data-ttu-id="6d3e4-126">O nome para exibição de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="6d3e4-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="6d3e4-127">ParentInstanceId</span></span>|<span data-ttu-id="6d3e4-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="6d3e4-128">xs:string</span></span>|<span data-ttu-id="6d3e4-129">A identificação de instância de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="6d3e4-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="6d3e4-130">CompletedActivity</span></span>|<span data-ttu-id="6d3e4-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="6d3e4-131">xs:string</span></span>|<span data-ttu-id="6d3e4-132">O nome do tipo de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="6d3e4-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="6d3e4-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="6d3e4-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="6d3e4-134">xs:string</span></span>|<span data-ttu-id="6d3e4-135">O nome para exibição de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="6d3e4-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="6d3e4-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="6d3e4-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="6d3e4-137">xs:string</span></span>|<span data-ttu-id="6d3e4-138">A identificação de instância de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="6d3e4-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6d3e4-139">AppDomain</span></span>|<span data-ttu-id="6d3e4-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="6d3e4-140">xs:string</span></span>|<span data-ttu-id="6d3e4-141">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
