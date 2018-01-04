---
title: 1035 - RuntimeTransactionSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a64a8a4ab6212a5e83b59fd7523df9cd875e7b87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="c13ec-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="c13ec-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="c13ec-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c13ec-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c13ec-104">ID</span><span class="sxs-lookup"><span data-stu-id="c13ec-104">ID</span></span>|<span data-ttu-id="c13ec-105">1035</span><span class="sxs-lookup"><span data-stu-id="c13ec-105">1035</span></span>|  
|<span data-ttu-id="c13ec-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="c13ec-106">Keywords</span></span>|<span data-ttu-id="c13ec-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c13ec-107">WFRuntime</span></span>|  
|<span data-ttu-id="c13ec-108">Nível</span><span class="sxs-lookup"><span data-stu-id="c13ec-108">Level</span></span>|<span data-ttu-id="c13ec-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="c13ec-109">Verbose</span></span>|  
|<span data-ttu-id="c13ec-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c13ec-110">Channel</span></span>|<span data-ttu-id="c13ec-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="c13ec-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c13ec-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c13ec-112">Description</span></span>  
 <span data-ttu-id="c13ec-113">Indica que uma atividade definiu a transação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c13ec-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c13ec-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c13ec-114">Message</span></span>  
 <span data-ttu-id="c13ec-115">A transação de tempo de execução foi definida pela atividade '%1', DisplayName: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="c13ec-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="c13ec-116">Execução isolada à atividade '%4', DisplayName: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="c13ec-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c13ec-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c13ec-117">Details</span></span>  
  
|<span data-ttu-id="c13ec-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="c13ec-118">Data Item Name</span></span>|<span data-ttu-id="c13ec-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="c13ec-119">Data Item Type</span></span>|<span data-ttu-id="c13ec-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="c13ec-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c13ec-121">Atividade</span><span class="sxs-lookup"><span data-stu-id="c13ec-121">Activity</span></span>|<span data-ttu-id="c13ec-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="c13ec-122">xs:string</span></span>|<span data-ttu-id="c13ec-123">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="c13ec-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="c13ec-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c13ec-124">DisplayName</span></span>|<span data-ttu-id="c13ec-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="c13ec-125">xs:string</span></span>|<span data-ttu-id="c13ec-126">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="c13ec-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="c13ec-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c13ec-127">InstanceId</span></span>|<span data-ttu-id="c13ec-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="c13ec-128">xs:string</span></span>|<span data-ttu-id="c13ec-129">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="c13ec-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c13ec-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="c13ec-130">IsolatedActivity</span></span>|<span data-ttu-id="c13ec-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="c13ec-131">xs:string</span></span>|<span data-ttu-id="c13ec-132">O nome do tipo de que a atividade isolada a transação está.</span><span class="sxs-lookup"><span data-stu-id="c13ec-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="c13ec-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="c13ec-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="c13ec-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="c13ec-134">xs:string</span></span>|<span data-ttu-id="c13ec-135">O nome para exibição de que a atividade isolada a transação está.</span><span class="sxs-lookup"><span data-stu-id="c13ec-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="c13ec-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="c13ec-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="c13ec-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="c13ec-137">xs:string</span></span>|<span data-ttu-id="c13ec-138">A identificação de instância de que a atividade isolada a transação está.</span><span class="sxs-lookup"><span data-stu-id="c13ec-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="c13ec-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c13ec-139">AppDomain</span></span>|<span data-ttu-id="c13ec-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="c13ec-140">xs:string</span></span>|<span data-ttu-id="c13ec-141">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c13ec-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
