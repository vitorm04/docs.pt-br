---
title: 1017 - ScheduleCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a632d59ddd75b375ff5e828a9f35aeecb0118f1c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="d54e5-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="d54e5-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="d54e5-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d54e5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d54e5-104">ID</span><span class="sxs-lookup"><span data-stu-id="d54e5-104">ID</span></span>|<span data-ttu-id="d54e5-105">1017</span><span class="sxs-lookup"><span data-stu-id="d54e5-105">1017</span></span>|  
|<span data-ttu-id="d54e5-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="d54e5-106">Keywords</span></span>|<span data-ttu-id="d54e5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d54e5-107">WFRuntime</span></span>|  
|<span data-ttu-id="d54e5-108">Nível</span><span class="sxs-lookup"><span data-stu-id="d54e5-108">Level</span></span>|<span data-ttu-id="d54e5-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="d54e5-109">Verbose</span></span>|  
|<span data-ttu-id="d54e5-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d54e5-110">Channel</span></span>|<span data-ttu-id="d54e5-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="d54e5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d54e5-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d54e5-112">Description</span></span>  
 <span data-ttu-id="d54e5-113">Indica que um CancelActivityWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="d54e5-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d54e5-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d54e5-114">Message</span></span>  
 <span data-ttu-id="d54e5-115">Um CancelActivityWorkItem foi agendada para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="d54e5-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d54e5-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d54e5-116">Details</span></span>  
  
|<span data-ttu-id="d54e5-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="d54e5-117">Data Item Name</span></span>|<span data-ttu-id="d54e5-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="d54e5-118">Data Item Type</span></span>|<span data-ttu-id="d54e5-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d54e5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d54e5-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="d54e5-120">Activity</span></span>|<span data-ttu-id="d54e5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d54e5-121">xs:string</span></span>|<span data-ttu-id="d54e5-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="d54e5-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="d54e5-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d54e5-123">DisplayName</span></span>|<span data-ttu-id="d54e5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d54e5-124">xs:string</span></span>|<span data-ttu-id="d54e5-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="d54e5-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="d54e5-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="d54e5-126">InstanceId</span></span>|<span data-ttu-id="d54e5-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="d54e5-127">xs:string</span></span>|<span data-ttu-id="d54e5-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="d54e5-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="d54e5-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d54e5-129">AppDomain</span></span>|<span data-ttu-id="d54e5-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="d54e5-130">xs:string</span></span>|<span data-ttu-id="d54e5-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d54e5-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
