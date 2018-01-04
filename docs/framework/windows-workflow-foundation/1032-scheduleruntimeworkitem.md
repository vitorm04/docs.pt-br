---
title: 1032 - ScheduleRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81cc73a5ab58e90f1a0ee5bdaf9a491d20206fb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="2a8b3-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="2a8b3-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2a8b3-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2a8b3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2a8b3-104">ID</span><span class="sxs-lookup"><span data-stu-id="2a8b3-104">ID</span></span>|<span data-ttu-id="2a8b3-105">1032</span><span class="sxs-lookup"><span data-stu-id="2a8b3-105">1032</span></span>|  
|<span data-ttu-id="2a8b3-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="2a8b3-106">Keywords</span></span>|<span data-ttu-id="2a8b3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2a8b3-107">WFRuntime</span></span>|  
|<span data-ttu-id="2a8b3-108">Nível</span><span class="sxs-lookup"><span data-stu-id="2a8b3-108">Level</span></span>|<span data-ttu-id="2a8b3-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="2a8b3-109">Verbose</span></span>|  
|<span data-ttu-id="2a8b3-110">Canal</span><span class="sxs-lookup"><span data-stu-id="2a8b3-110">Channel</span></span>|<span data-ttu-id="2a8b3-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="2a8b3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2a8b3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a8b3-112">Description</span></span>  
 <span data-ttu-id="2a8b3-113">Indica que um RuntimeWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="2a8b3-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2a8b3-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="2a8b3-114">Message</span></span>  
 <span data-ttu-id="2a8b3-115">Um item de trabalho de tempo de execução foi agendada para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="2a8b3-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2a8b3-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2a8b3-116">Details</span></span>  
  
|<span data-ttu-id="2a8b3-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="2a8b3-117">Data Item Name</span></span>|<span data-ttu-id="2a8b3-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="2a8b3-118">Data Item Type</span></span>|<span data-ttu-id="2a8b3-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a8b3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2a8b3-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="2a8b3-120">Activity</span></span>|<span data-ttu-id="2a8b3-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="2a8b3-121">xs:string</span></span>|<span data-ttu-id="2a8b3-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="2a8b3-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="2a8b3-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="2a8b3-123">DisplayName</span></span>|<span data-ttu-id="2a8b3-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="2a8b3-124">xs:string</span></span>|<span data-ttu-id="2a8b3-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="2a8b3-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="2a8b3-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="2a8b3-126">InstanceId</span></span>|<span data-ttu-id="2a8b3-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="2a8b3-127">xs:string</span></span>|<span data-ttu-id="2a8b3-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="2a8b3-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="2a8b3-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2a8b3-129">AppDomain</span></span>|<span data-ttu-id="2a8b3-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="2a8b3-130">xs:string</span></span>|<span data-ttu-id="2a8b3-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2a8b3-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
