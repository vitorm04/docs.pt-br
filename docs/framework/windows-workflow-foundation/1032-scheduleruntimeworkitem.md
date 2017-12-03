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
ms.openlocfilehash: d2a150b9e9c78a9ce1f5e20b962a58ef2d5dde9d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="5acaa-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="5acaa-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="5acaa-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5acaa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5acaa-104">ID</span><span class="sxs-lookup"><span data-stu-id="5acaa-104">ID</span></span>|<span data-ttu-id="5acaa-105">1032</span><span class="sxs-lookup"><span data-stu-id="5acaa-105">1032</span></span>|  
|<span data-ttu-id="5acaa-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="5acaa-106">Keywords</span></span>|<span data-ttu-id="5acaa-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5acaa-107">WFRuntime</span></span>|  
|<span data-ttu-id="5acaa-108">Nível</span><span class="sxs-lookup"><span data-stu-id="5acaa-108">Level</span></span>|<span data-ttu-id="5acaa-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="5acaa-109">Verbose</span></span>|  
|<span data-ttu-id="5acaa-110">Canal</span><span class="sxs-lookup"><span data-stu-id="5acaa-110">Channel</span></span>|<span data-ttu-id="5acaa-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="5acaa-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5acaa-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5acaa-112">Description</span></span>  
 <span data-ttu-id="5acaa-113">Indica que um RuntimeWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="5acaa-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5acaa-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="5acaa-114">Message</span></span>  
 <span data-ttu-id="5acaa-115">Um item de trabalho de tempo de execução foi agendada para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="5acaa-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5acaa-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5acaa-116">Details</span></span>  
  
|<span data-ttu-id="5acaa-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="5acaa-117">Data Item Name</span></span>|<span data-ttu-id="5acaa-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="5acaa-118">Data Item Type</span></span>|<span data-ttu-id="5acaa-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="5acaa-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5acaa-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="5acaa-120">Activity</span></span>|<span data-ttu-id="5acaa-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="5acaa-121">xs:string</span></span>|<span data-ttu-id="5acaa-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="5acaa-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="5acaa-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="5acaa-123">DisplayName</span></span>|<span data-ttu-id="5acaa-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="5acaa-124">xs:string</span></span>|<span data-ttu-id="5acaa-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="5acaa-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="5acaa-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="5acaa-126">InstanceId</span></span>|<span data-ttu-id="5acaa-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="5acaa-127">xs:string</span></span>|<span data-ttu-id="5acaa-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="5acaa-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="5acaa-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5acaa-129">AppDomain</span></span>|<span data-ttu-id="5acaa-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="5acaa-130">xs:string</span></span>|<span data-ttu-id="5acaa-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5acaa-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
