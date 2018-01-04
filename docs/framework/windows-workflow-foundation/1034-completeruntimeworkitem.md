---
title: 1034 - CompleteRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 743b16232e239929f75e269faa16799a37043495
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="860b4-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="860b4-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="860b4-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="860b4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="860b4-104">ID</span><span class="sxs-lookup"><span data-stu-id="860b4-104">ID</span></span>|<span data-ttu-id="860b4-105">1034</span><span class="sxs-lookup"><span data-stu-id="860b4-105">1034</span></span>|  
|<span data-ttu-id="860b4-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="860b4-106">Keywords</span></span>|<span data-ttu-id="860b4-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="860b4-107">WFRuntime</span></span>|  
|<span data-ttu-id="860b4-108">Nível</span><span class="sxs-lookup"><span data-stu-id="860b4-108">Level</span></span>|<span data-ttu-id="860b4-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="860b4-109">Verbose</span></span>|  
|<span data-ttu-id="860b4-110">Canal</span><span class="sxs-lookup"><span data-stu-id="860b4-110">Channel</span></span>|<span data-ttu-id="860b4-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="860b4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="860b4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="860b4-112">Description</span></span>  
 <span data-ttu-id="860b4-113">Indica que um RuntimeWorkItem terminado.</span><span class="sxs-lookup"><span data-stu-id="860b4-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="860b4-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="860b4-114">Message</span></span>  
 <span data-ttu-id="860b4-115">Um item de trabalho de tempo de execução concluiu para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="860b4-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="860b4-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="860b4-116">Details</span></span>  
  
|<span data-ttu-id="860b4-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="860b4-117">Data Item Name</span></span>|<span data-ttu-id="860b4-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="860b4-118">Data Item Type</span></span>|<span data-ttu-id="860b4-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="860b4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="860b4-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="860b4-120">Activity</span></span>|<span data-ttu-id="860b4-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="860b4-121">xs:string</span></span>|<span data-ttu-id="860b4-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="860b4-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="860b4-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="860b4-123">DisplayName</span></span>|<span data-ttu-id="860b4-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="860b4-124">xs:string</span></span>|<span data-ttu-id="860b4-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="860b4-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="860b4-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="860b4-126">InstanceId</span></span>|<span data-ttu-id="860b4-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="860b4-127">xs:string</span></span>|<span data-ttu-id="860b4-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="860b4-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="860b4-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="860b4-129">AppDomain</span></span>|<span data-ttu-id="860b4-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="860b4-130">xs:string</span></span>|<span data-ttu-id="860b4-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="860b4-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
