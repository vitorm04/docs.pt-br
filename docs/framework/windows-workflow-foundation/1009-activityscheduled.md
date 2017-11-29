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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d9463fbf2e7f2ac3424488dc3fca322a91d11126
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="5d574-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="5d574-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="5d574-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5d574-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5d574-104">ID</span><span class="sxs-lookup"><span data-stu-id="5d574-104">ID</span></span>|<span data-ttu-id="5d574-105">1009</span><span class="sxs-lookup"><span data-stu-id="5d574-105">1009</span></span>|  
|<span data-ttu-id="5d574-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="5d574-106">Keywords</span></span>|<span data-ttu-id="5d574-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5d574-107">WFRuntime</span></span>|  
|<span data-ttu-id="5d574-108">Nível</span><span class="sxs-lookup"><span data-stu-id="5d574-108">Level</span></span>|<span data-ttu-id="5d574-109">Informações</span><span class="sxs-lookup"><span data-stu-id="5d574-109">Information</span></span>|  
|<span data-ttu-id="5d574-110">Canal</span><span class="sxs-lookup"><span data-stu-id="5d574-110">Channel</span></span>|<span data-ttu-id="5d574-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="5d574-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5d574-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d574-112">Description</span></span>  
 <span data-ttu-id="5d574-113">Indica que uma atividade está sendo agendada para a execução.</span><span class="sxs-lookup"><span data-stu-id="5d574-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5d574-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="5d574-114">Message</span></span>  
 <span data-ttu-id="5d574-115">Atividade pai “%1", DisplayName: “%2", InstanceId: “%3" agendaram a atividade filho “%4", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="5d574-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5d574-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5d574-116">Details</span></span>  
  
|<span data-ttu-id="5d574-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="5d574-117">Data Item Name</span></span>|<span data-ttu-id="5d574-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="5d574-118">Data Item Type</span></span>|<span data-ttu-id="5d574-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d574-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5d574-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="5d574-120">ParentActivity</span></span>|<span data-ttu-id="5d574-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="5d574-121">xs:string</span></span>|<span data-ttu-id="5d574-122">O nome do tipo de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="5d574-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="5d574-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="5d574-123">ParentDisplayName</span></span>|<span data-ttu-id="5d574-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="5d574-124">xs:string</span></span>|<span data-ttu-id="5d574-125">O nome para exibição de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="5d574-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="5d574-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="5d574-126">ParentInstanceId</span></span>|<span data-ttu-id="5d574-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="5d574-127">xs:string</span></span>|<span data-ttu-id="5d574-128">A identificação de instância de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="5d574-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="5d574-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="5d574-129">ChildActivity</span></span>|<span data-ttu-id="5d574-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="5d574-130">xs:string</span></span>|<span data-ttu-id="5d574-131">O nome do tipo de atividade filho agendada.</span><span class="sxs-lookup"><span data-stu-id="5d574-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="5d574-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="5d574-132">ChildDisplayName</span></span>|<span data-ttu-id="5d574-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="5d574-133">xs:string</span></span>|<span data-ttu-id="5d574-134">O nome para exibição de atividade filho agendada.</span><span class="sxs-lookup"><span data-stu-id="5d574-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="5d574-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="5d574-135">ChildInstanceId</span></span>|<span data-ttu-id="5d574-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="5d574-136">xs:string</span></span>|<span data-ttu-id="5d574-137">A identificação de instância de atividade filho agendada.</span><span class="sxs-lookup"><span data-stu-id="5d574-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="5d574-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5d574-138">AppDomain</span></span>|<span data-ttu-id="5d574-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="5d574-139">xs:string</span></span>|<span data-ttu-id="5d574-140">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5d574-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
