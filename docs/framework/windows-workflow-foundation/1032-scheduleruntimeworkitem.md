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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4de69b1fc2647d7723db8aebb02942938db7478f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="96a1c-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="96a1c-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="96a1c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="96a1c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="96a1c-104">ID</span><span class="sxs-lookup"><span data-stu-id="96a1c-104">ID</span></span>|<span data-ttu-id="96a1c-105">1032</span><span class="sxs-lookup"><span data-stu-id="96a1c-105">1032</span></span>|  
|<span data-ttu-id="96a1c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="96a1c-106">Keywords</span></span>|<span data-ttu-id="96a1c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="96a1c-107">WFRuntime</span></span>|  
|<span data-ttu-id="96a1c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="96a1c-108">Level</span></span>|<span data-ttu-id="96a1c-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="96a1c-109">Verbose</span></span>|  
|<span data-ttu-id="96a1c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="96a1c-110">Channel</span></span>|<span data-ttu-id="96a1c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="96a1c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="96a1c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="96a1c-112">Description</span></span>  
 <span data-ttu-id="96a1c-113">Indica que um RuntimeWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="96a1c-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="96a1c-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="96a1c-114">Message</span></span>  
 <span data-ttu-id="96a1c-115">Um item de trabalho de tempo de execução foi agendada para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="96a1c-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="96a1c-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="96a1c-116">Details</span></span>  
  
|<span data-ttu-id="96a1c-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="96a1c-117">Data Item Name</span></span>|<span data-ttu-id="96a1c-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="96a1c-118">Data Item Type</span></span>|<span data-ttu-id="96a1c-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="96a1c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="96a1c-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="96a1c-120">Activity</span></span>|<span data-ttu-id="96a1c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="96a1c-121">xs:string</span></span>|<span data-ttu-id="96a1c-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="96a1c-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="96a1c-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="96a1c-123">DisplayName</span></span>|<span data-ttu-id="96a1c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="96a1c-124">xs:string</span></span>|<span data-ttu-id="96a1c-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="96a1c-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="96a1c-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="96a1c-126">InstanceId</span></span>|<span data-ttu-id="96a1c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="96a1c-127">xs:string</span></span>|<span data-ttu-id="96a1c-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="96a1c-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="96a1c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="96a1c-129">AppDomain</span></span>|<span data-ttu-id="96a1c-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="96a1c-130">xs:string</span></span>|<span data-ttu-id="96a1c-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="96a1c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
