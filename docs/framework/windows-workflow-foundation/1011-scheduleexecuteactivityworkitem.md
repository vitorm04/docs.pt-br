---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec89acb9d83a28ac280db7c3d536bfe63669fa97
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="b5f43-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="b5f43-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="b5f43-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b5f43-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5f43-104">ID</span><span class="sxs-lookup"><span data-stu-id="b5f43-104">ID</span></span>|<span data-ttu-id="b5f43-105">1011</span><span class="sxs-lookup"><span data-stu-id="b5f43-105">1011</span></span>|  
|<span data-ttu-id="b5f43-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="b5f43-106">Keywords</span></span>|<span data-ttu-id="b5f43-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b5f43-107">WFRuntime</span></span>|  
|<span data-ttu-id="b5f43-108">Nível</span><span class="sxs-lookup"><span data-stu-id="b5f43-108">Level</span></span>|<span data-ttu-id="b5f43-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="b5f43-109">Verbose</span></span>|  
|<span data-ttu-id="b5f43-110">Canal</span><span class="sxs-lookup"><span data-stu-id="b5f43-110">Channel</span></span>|<span data-ttu-id="b5f43-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="b5f43-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b5f43-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5f43-112">Description</span></span>  
 <span data-ttu-id="b5f43-113">Indica que um ExecuteActivityWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="b5f43-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b5f43-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="b5f43-114">Message</span></span>  
 <span data-ttu-id="b5f43-115">Um ExecuteActivityWorkItem foi agendada para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="b5f43-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b5f43-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="b5f43-116">Details</span></span>  
  
|<span data-ttu-id="b5f43-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="b5f43-117">Data Item Name</span></span>|<span data-ttu-id="b5f43-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="b5f43-118">Data Item Type</span></span>|<span data-ttu-id="b5f43-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5f43-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b5f43-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="b5f43-120">Activity</span></span>|<span data-ttu-id="b5f43-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="b5f43-121">xs:string</span></span>|<span data-ttu-id="b5f43-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="b5f43-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="b5f43-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b5f43-123">DisplayName</span></span>|<span data-ttu-id="b5f43-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="b5f43-124">xs:string</span></span>|<span data-ttu-id="b5f43-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="b5f43-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="b5f43-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="b5f43-126">InstanceId</span></span>|<span data-ttu-id="b5f43-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="b5f43-127">xs:string</span></span>|<span data-ttu-id="b5f43-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="b5f43-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="b5f43-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b5f43-129">AppDomain</span></span>|<span data-ttu-id="b5f43-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="b5f43-130">xs:string</span></span>|<span data-ttu-id="b5f43-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b5f43-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
