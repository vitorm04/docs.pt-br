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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3dc30100cb134740f51e6b2b38c00b2054d2ab0a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="04217-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="04217-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="04217-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="04217-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="04217-104">ID</span><span class="sxs-lookup"><span data-stu-id="04217-104">ID</span></span>|<span data-ttu-id="04217-105">1021</span><span class="sxs-lookup"><span data-stu-id="04217-105">1021</span></span>|  
|<span data-ttu-id="04217-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="04217-106">Keywords</span></span>|<span data-ttu-id="04217-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="04217-107">WFRuntime</span></span>|  
|<span data-ttu-id="04217-108">Nível</span><span class="sxs-lookup"><span data-stu-id="04217-108">Level</span></span>|<span data-ttu-id="04217-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="04217-109">Verbose</span></span>|  
|<span data-ttu-id="04217-110">Canal</span><span class="sxs-lookup"><span data-stu-id="04217-110">Channel</span></span>|<span data-ttu-id="04217-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="04217-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="04217-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="04217-112">Description</span></span>  
 <span data-ttu-id="04217-113">Indica que um BookmarkWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="04217-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="04217-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="04217-114">Message</span></span>  
 <span data-ttu-id="04217-115">Um BookmarkWorkItem foi agendado para a atividade '%1', DisplayName: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="04217-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="04217-116">BookmarkName: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="04217-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="04217-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="04217-117">Details</span></span>  
  
|<span data-ttu-id="04217-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="04217-118">Data Item Name</span></span>|<span data-ttu-id="04217-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="04217-119">Data Item Type</span></span>|<span data-ttu-id="04217-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="04217-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="04217-121">Atividade</span><span class="sxs-lookup"><span data-stu-id="04217-121">Activity</span></span>|<span data-ttu-id="04217-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="04217-122">xs:string</span></span>|<span data-ttu-id="04217-123">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="04217-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="04217-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="04217-124">DisplayName</span></span>|<span data-ttu-id="04217-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="04217-125">xs:string</span></span>|<span data-ttu-id="04217-126">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="04217-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="04217-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="04217-127">InstanceId</span></span>|<span data-ttu-id="04217-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="04217-128">xs:string</span></span>|<span data-ttu-id="04217-129">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="04217-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="04217-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="04217-130">BookmarkName</span></span>|<span data-ttu-id="04217-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="04217-131">xs:string</span></span>|<span data-ttu-id="04217-132">O nome do indicador.</span><span class="sxs-lookup"><span data-stu-id="04217-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="04217-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="04217-133">BookmarkScope</span></span>|<span data-ttu-id="04217-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="04217-134">xs:string</span></span>|<span data-ttu-id="04217-135">O escopo do indexador.</span><span class="sxs-lookup"><span data-stu-id="04217-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="04217-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="04217-136">AppDomain</span></span>|<span data-ttu-id="04217-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="04217-137">xs:string</span></span>|<span data-ttu-id="04217-138">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="04217-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
