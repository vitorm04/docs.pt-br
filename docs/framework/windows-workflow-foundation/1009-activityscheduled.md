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
ms.openlocfilehash: bdaa8ca4efeffb3895e0056303721b13cdc1ae27
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="17eb7-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="17eb7-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="17eb7-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="17eb7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="17eb7-104">ID</span><span class="sxs-lookup"><span data-stu-id="17eb7-104">ID</span></span>|<span data-ttu-id="17eb7-105">1009</span><span class="sxs-lookup"><span data-stu-id="17eb7-105">1009</span></span>|  
|<span data-ttu-id="17eb7-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="17eb7-106">Keywords</span></span>|<span data-ttu-id="17eb7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="17eb7-107">WFRuntime</span></span>|  
|<span data-ttu-id="17eb7-108">Nível</span><span class="sxs-lookup"><span data-stu-id="17eb7-108">Level</span></span>|<span data-ttu-id="17eb7-109">Informações</span><span class="sxs-lookup"><span data-stu-id="17eb7-109">Information</span></span>|  
|<span data-ttu-id="17eb7-110">Canal</span><span class="sxs-lookup"><span data-stu-id="17eb7-110">Channel</span></span>|<span data-ttu-id="17eb7-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="17eb7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="17eb7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="17eb7-112">Description</span></span>  
 <span data-ttu-id="17eb7-113">Indica que uma atividade está sendo agendada para a execução.</span><span class="sxs-lookup"><span data-stu-id="17eb7-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="17eb7-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="17eb7-114">Message</span></span>  
 <span data-ttu-id="17eb7-115">Atividade pai “%1", DisplayName: “%2", InstanceId: “%3" agendaram a atividade filho “%4", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="17eb7-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="17eb7-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="17eb7-116">Details</span></span>  
  
|<span data-ttu-id="17eb7-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="17eb7-117">Data Item Name</span></span>|<span data-ttu-id="17eb7-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="17eb7-118">Data Item Type</span></span>|<span data-ttu-id="17eb7-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="17eb7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="17eb7-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="17eb7-120">ParentActivity</span></span>|<span data-ttu-id="17eb7-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="17eb7-121">xs:string</span></span>|<span data-ttu-id="17eb7-122">O nome do tipo de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="17eb7-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="17eb7-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="17eb7-123">ParentDisplayName</span></span>|<span data-ttu-id="17eb7-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="17eb7-124">xs:string</span></span>|<span data-ttu-id="17eb7-125">O nome para exibição de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="17eb7-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="17eb7-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="17eb7-126">ParentInstanceId</span></span>|<span data-ttu-id="17eb7-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="17eb7-127">xs:string</span></span>|<span data-ttu-id="17eb7-128">A identificação de instância de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="17eb7-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="17eb7-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="17eb7-129">ChildActivity</span></span>|<span data-ttu-id="17eb7-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="17eb7-130">xs:string</span></span>|<span data-ttu-id="17eb7-131">O nome do tipo de atividade filho agendada.</span><span class="sxs-lookup"><span data-stu-id="17eb7-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="17eb7-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="17eb7-132">ChildDisplayName</span></span>|<span data-ttu-id="17eb7-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="17eb7-133">xs:string</span></span>|<span data-ttu-id="17eb7-134">O nome para exibição de atividade filho agendada.</span><span class="sxs-lookup"><span data-stu-id="17eb7-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="17eb7-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="17eb7-135">ChildInstanceId</span></span>|<span data-ttu-id="17eb7-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="17eb7-136">xs:string</span></span>|<span data-ttu-id="17eb7-137">A identificação de instância de atividade filho agendada.</span><span class="sxs-lookup"><span data-stu-id="17eb7-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="17eb7-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="17eb7-138">AppDomain</span></span>|<span data-ttu-id="17eb7-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="17eb7-139">xs:string</span></span>|<span data-ttu-id="17eb7-140">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="17eb7-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
