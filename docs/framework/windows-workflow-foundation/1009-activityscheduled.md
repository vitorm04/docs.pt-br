---
title: 1009 - ActivityScheduled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a0d8cc3d17ecd13d9312b42554ef5347cccf213
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="84f3a-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="84f3a-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="84f3a-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="84f3a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="84f3a-104">ID</span><span class="sxs-lookup"><span data-stu-id="84f3a-104">ID</span></span>|<span data-ttu-id="84f3a-105">1009</span><span class="sxs-lookup"><span data-stu-id="84f3a-105">1009</span></span>|  
|<span data-ttu-id="84f3a-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="84f3a-106">Keywords</span></span>|<span data-ttu-id="84f3a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="84f3a-107">WFRuntime</span></span>|  
|<span data-ttu-id="84f3a-108">Nível</span><span class="sxs-lookup"><span data-stu-id="84f3a-108">Level</span></span>|<span data-ttu-id="84f3a-109">Informações</span><span class="sxs-lookup"><span data-stu-id="84f3a-109">Information</span></span>|  
|<span data-ttu-id="84f3a-110">Canal</span><span class="sxs-lookup"><span data-stu-id="84f3a-110">Channel</span></span>|<span data-ttu-id="84f3a-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="84f3a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="84f3a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="84f3a-112">Description</span></span>  
 <span data-ttu-id="84f3a-113">Indica que uma atividade está sendo agendada para a execução.</span><span class="sxs-lookup"><span data-stu-id="84f3a-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="84f3a-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="84f3a-114">Message</span></span>  
 <span data-ttu-id="84f3a-115">Atividade pai “%1", DisplayName: “%2", InstanceId: “%3" agendaram a atividade filho “%4", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="84f3a-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="84f3a-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="84f3a-116">Details</span></span>  
  
|<span data-ttu-id="84f3a-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="84f3a-117">Data Item Name</span></span>|<span data-ttu-id="84f3a-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="84f3a-118">Data Item Type</span></span>|<span data-ttu-id="84f3a-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="84f3a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="84f3a-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="84f3a-120">ParentActivity</span></span>|<span data-ttu-id="84f3a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="84f3a-121">xs:string</span></span>|<span data-ttu-id="84f3a-122">O nome do tipo de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="84f3a-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="84f3a-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="84f3a-123">ParentDisplayName</span></span>|<span data-ttu-id="84f3a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="84f3a-124">xs:string</span></span>|<span data-ttu-id="84f3a-125">O nome para exibição de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="84f3a-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="84f3a-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="84f3a-126">ParentInstanceId</span></span>|<span data-ttu-id="84f3a-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="84f3a-127">xs:string</span></span>|<span data-ttu-id="84f3a-128">A identificação de instância de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="84f3a-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="84f3a-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="84f3a-129">ChildActivity</span></span>|<span data-ttu-id="84f3a-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="84f3a-130">xs:string</span></span>|<span data-ttu-id="84f3a-131">O nome do tipo de atividade filho agendada.</span><span class="sxs-lookup"><span data-stu-id="84f3a-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="84f3a-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="84f3a-132">ChildDisplayName</span></span>|<span data-ttu-id="84f3a-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="84f3a-133">xs:string</span></span>|<span data-ttu-id="84f3a-134">O nome para exibição de atividade filho agendada.</span><span class="sxs-lookup"><span data-stu-id="84f3a-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="84f3a-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="84f3a-135">ChildInstanceId</span></span>|<span data-ttu-id="84f3a-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="84f3a-136">xs:string</span></span>|<span data-ttu-id="84f3a-137">A identificação de instância de atividade filho agendada.</span><span class="sxs-lookup"><span data-stu-id="84f3a-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="84f3a-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="84f3a-138">AppDomain</span></span>|<span data-ttu-id="84f3a-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="84f3a-139">xs:string</span></span>|<span data-ttu-id="84f3a-140">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="84f3a-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
