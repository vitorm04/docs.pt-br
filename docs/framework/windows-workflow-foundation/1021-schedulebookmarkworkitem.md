---
title: 1021 - ScheduleBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61c67792f807907f58480f3bfa3d192b811766b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="fbec0-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="fbec0-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="fbec0-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="fbec0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fbec0-104">ID</span><span class="sxs-lookup"><span data-stu-id="fbec0-104">ID</span></span>|<span data-ttu-id="fbec0-105">1021</span><span class="sxs-lookup"><span data-stu-id="fbec0-105">1021</span></span>|  
|<span data-ttu-id="fbec0-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="fbec0-106">Keywords</span></span>|<span data-ttu-id="fbec0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fbec0-107">WFRuntime</span></span>|  
|<span data-ttu-id="fbec0-108">Nível</span><span class="sxs-lookup"><span data-stu-id="fbec0-108">Level</span></span>|<span data-ttu-id="fbec0-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="fbec0-109">Verbose</span></span>|  
|<span data-ttu-id="fbec0-110">Canal</span><span class="sxs-lookup"><span data-stu-id="fbec0-110">Channel</span></span>|<span data-ttu-id="fbec0-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="fbec0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fbec0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbec0-112">Description</span></span>  
 <span data-ttu-id="fbec0-113">Indica que um BookmarkWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="fbec0-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fbec0-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="fbec0-114">Message</span></span>  
 <span data-ttu-id="fbec0-115">Um BookmarkWorkItem foi agendado para a atividade '%1', DisplayName: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="fbec0-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="fbec0-116">BookmarkName: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="fbec0-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fbec0-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="fbec0-117">Details</span></span>  
  
|<span data-ttu-id="fbec0-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="fbec0-118">Data Item Name</span></span>|<span data-ttu-id="fbec0-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="fbec0-119">Data Item Type</span></span>|<span data-ttu-id="fbec0-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbec0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fbec0-121">Atividade</span><span class="sxs-lookup"><span data-stu-id="fbec0-121">Activity</span></span>|<span data-ttu-id="fbec0-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="fbec0-122">xs:string</span></span>|<span data-ttu-id="fbec0-123">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="fbec0-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="fbec0-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="fbec0-124">DisplayName</span></span>|<span data-ttu-id="fbec0-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="fbec0-125">xs:string</span></span>|<span data-ttu-id="fbec0-126">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="fbec0-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="fbec0-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="fbec0-127">InstanceId</span></span>|<span data-ttu-id="fbec0-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="fbec0-128">xs:string</span></span>|<span data-ttu-id="fbec0-129">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="fbec0-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="fbec0-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="fbec0-130">BookmarkName</span></span>|<span data-ttu-id="fbec0-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="fbec0-131">xs:string</span></span>|<span data-ttu-id="fbec0-132">O nome do indicador.</span><span class="sxs-lookup"><span data-stu-id="fbec0-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="fbec0-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="fbec0-133">BookmarkScope</span></span>|<span data-ttu-id="fbec0-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="fbec0-134">xs:string</span></span>|<span data-ttu-id="fbec0-135">O escopo do indexador.</span><span class="sxs-lookup"><span data-stu-id="fbec0-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="fbec0-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fbec0-136">AppDomain</span></span>|<span data-ttu-id="fbec0-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="fbec0-137">xs:string</span></span>|<span data-ttu-id="fbec0-138">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fbec0-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
