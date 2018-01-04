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
ms.workload: dotnet
ms.openlocfilehash: b524f083c49f517c21c77da4f1d1488625a575b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="91220-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="91220-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="91220-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="91220-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="91220-104">ID</span><span class="sxs-lookup"><span data-stu-id="91220-104">ID</span></span>|<span data-ttu-id="91220-105">1017</span><span class="sxs-lookup"><span data-stu-id="91220-105">1017</span></span>|  
|<span data-ttu-id="91220-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="91220-106">Keywords</span></span>|<span data-ttu-id="91220-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="91220-107">WFRuntime</span></span>|  
|<span data-ttu-id="91220-108">Nível</span><span class="sxs-lookup"><span data-stu-id="91220-108">Level</span></span>|<span data-ttu-id="91220-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="91220-109">Verbose</span></span>|  
|<span data-ttu-id="91220-110">Canal</span><span class="sxs-lookup"><span data-stu-id="91220-110">Channel</span></span>|<span data-ttu-id="91220-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="91220-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="91220-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="91220-112">Description</span></span>  
 <span data-ttu-id="91220-113">Indica que um CancelActivityWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="91220-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="91220-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="91220-114">Message</span></span>  
 <span data-ttu-id="91220-115">Um CancelActivityWorkItem foi agendada para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="91220-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="91220-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="91220-116">Details</span></span>  
  
|<span data-ttu-id="91220-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="91220-117">Data Item Name</span></span>|<span data-ttu-id="91220-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="91220-118">Data Item Type</span></span>|<span data-ttu-id="91220-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="91220-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="91220-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="91220-120">Activity</span></span>|<span data-ttu-id="91220-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="91220-121">xs:string</span></span>|<span data-ttu-id="91220-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="91220-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="91220-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="91220-123">DisplayName</span></span>|<span data-ttu-id="91220-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="91220-124">xs:string</span></span>|<span data-ttu-id="91220-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="91220-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="91220-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="91220-126">InstanceId</span></span>|<span data-ttu-id="91220-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="91220-127">xs:string</span></span>|<span data-ttu-id="91220-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="91220-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="91220-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="91220-129">AppDomain</span></span>|<span data-ttu-id="91220-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="91220-130">xs:string</span></span>|<span data-ttu-id="91220-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="91220-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
