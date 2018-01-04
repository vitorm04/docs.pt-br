---
title: 1019 - CompleteCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 378f756003e45905e3697e2e9470aa1e582a2ad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="ae273-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="ae273-102">1019 - CompleteCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ae273-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ae273-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae273-104">ID</span><span class="sxs-lookup"><span data-stu-id="ae273-104">ID</span></span>|<span data-ttu-id="ae273-105">1019</span><span class="sxs-lookup"><span data-stu-id="ae273-105">1019</span></span>|  
|<span data-ttu-id="ae273-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="ae273-106">Keywords</span></span>|<span data-ttu-id="ae273-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ae273-107">WFRuntime</span></span>|  
|<span data-ttu-id="ae273-108">Nível</span><span class="sxs-lookup"><span data-stu-id="ae273-108">Level</span></span>|<span data-ttu-id="ae273-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="ae273-109">Verbose</span></span>|  
|<span data-ttu-id="ae273-110">Canal</span><span class="sxs-lookup"><span data-stu-id="ae273-110">Channel</span></span>|<span data-ttu-id="ae273-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="ae273-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ae273-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae273-112">Description</span></span>  
 <span data-ttu-id="ae273-113">Indica que um CancelActivityWorkItem terminado.</span><span class="sxs-lookup"><span data-stu-id="ae273-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ae273-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="ae273-114">Message</span></span>  
 <span data-ttu-id="ae273-115">Um CancelActivityWorkItem concluiu para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="ae273-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ae273-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ae273-116">Details</span></span>  
  
|<span data-ttu-id="ae273-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="ae273-117">Data Item Name</span></span>|<span data-ttu-id="ae273-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="ae273-118">Data Item Type</span></span>|<span data-ttu-id="ae273-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae273-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ae273-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="ae273-120">Activity</span></span>|<span data-ttu-id="ae273-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ae273-121">xs:string</span></span>|<span data-ttu-id="ae273-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="ae273-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="ae273-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ae273-123">DisplayName</span></span>|<span data-ttu-id="ae273-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ae273-124">xs:string</span></span>|<span data-ttu-id="ae273-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="ae273-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="ae273-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ae273-126">InstanceId</span></span>|<span data-ttu-id="ae273-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="ae273-127">xs:string</span></span>|<span data-ttu-id="ae273-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="ae273-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ae273-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ae273-129">AppDomain</span></span>|<span data-ttu-id="ae273-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="ae273-130">xs:string</span></span>|<span data-ttu-id="ae273-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ae273-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
