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
ms.openlocfilehash: 781f4b6d064ac90f762e10e03783422c64a1bf05
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="d78dd-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="d78dd-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="d78dd-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d78dd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d78dd-104">ID</span><span class="sxs-lookup"><span data-stu-id="d78dd-104">ID</span></span>|<span data-ttu-id="d78dd-105">1021</span><span class="sxs-lookup"><span data-stu-id="d78dd-105">1021</span></span>|  
|<span data-ttu-id="d78dd-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="d78dd-106">Keywords</span></span>|<span data-ttu-id="d78dd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d78dd-107">WFRuntime</span></span>|  
|<span data-ttu-id="d78dd-108">Nível</span><span class="sxs-lookup"><span data-stu-id="d78dd-108">Level</span></span>|<span data-ttu-id="d78dd-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="d78dd-109">Verbose</span></span>|  
|<span data-ttu-id="d78dd-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d78dd-110">Channel</span></span>|<span data-ttu-id="d78dd-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="d78dd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d78dd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d78dd-112">Description</span></span>  
 <span data-ttu-id="d78dd-113">Indica que um BookmarkWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="d78dd-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d78dd-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d78dd-114">Message</span></span>  
 <span data-ttu-id="d78dd-115">Um BookmarkWorkItem foi agendado para a atividade '%1', DisplayName: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="d78dd-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="d78dd-116">BookmarkName: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="d78dd-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d78dd-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d78dd-117">Details</span></span>  
  
|<span data-ttu-id="d78dd-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="d78dd-118">Data Item Name</span></span>|<span data-ttu-id="d78dd-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="d78dd-119">Data Item Type</span></span>|<span data-ttu-id="d78dd-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="d78dd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d78dd-121">Atividade</span><span class="sxs-lookup"><span data-stu-id="d78dd-121">Activity</span></span>|<span data-ttu-id="d78dd-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="d78dd-122">xs:string</span></span>|<span data-ttu-id="d78dd-123">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="d78dd-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="d78dd-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d78dd-124">DisplayName</span></span>|<span data-ttu-id="d78dd-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="d78dd-125">xs:string</span></span>|<span data-ttu-id="d78dd-126">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="d78dd-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="d78dd-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="d78dd-127">InstanceId</span></span>|<span data-ttu-id="d78dd-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="d78dd-128">xs:string</span></span>|<span data-ttu-id="d78dd-129">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="d78dd-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="d78dd-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="d78dd-130">BookmarkName</span></span>|<span data-ttu-id="d78dd-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="d78dd-131">xs:string</span></span>|<span data-ttu-id="d78dd-132">O nome do indicador.</span><span class="sxs-lookup"><span data-stu-id="d78dd-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="d78dd-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="d78dd-133">BookmarkScope</span></span>|<span data-ttu-id="d78dd-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="d78dd-134">xs:string</span></span>|<span data-ttu-id="d78dd-135">O escopo do indexador.</span><span class="sxs-lookup"><span data-stu-id="d78dd-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="d78dd-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d78dd-136">AppDomain</span></span>|<span data-ttu-id="d78dd-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="d78dd-137">xs:string</span></span>|<span data-ttu-id="d78dd-138">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d78dd-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
