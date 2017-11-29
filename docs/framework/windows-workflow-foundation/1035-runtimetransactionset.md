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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c3fcd93dbc30b20f7822a54babde8277e32d8335
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="19050-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="19050-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="19050-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="19050-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="19050-104">ID</span><span class="sxs-lookup"><span data-stu-id="19050-104">ID</span></span>|<span data-ttu-id="19050-105">1035</span><span class="sxs-lookup"><span data-stu-id="19050-105">1035</span></span>|  
|<span data-ttu-id="19050-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="19050-106">Keywords</span></span>|<span data-ttu-id="19050-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="19050-107">WFRuntime</span></span>|  
|<span data-ttu-id="19050-108">Nível</span><span class="sxs-lookup"><span data-stu-id="19050-108">Level</span></span>|<span data-ttu-id="19050-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="19050-109">Verbose</span></span>|  
|<span data-ttu-id="19050-110">Canal</span><span class="sxs-lookup"><span data-stu-id="19050-110">Channel</span></span>|<span data-ttu-id="19050-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="19050-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="19050-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="19050-112">Description</span></span>  
 <span data-ttu-id="19050-113">Indica que uma atividade definiu a transação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="19050-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="19050-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="19050-114">Message</span></span>  
 <span data-ttu-id="19050-115">A transação de tempo de execução foi definida pela atividade '%1', DisplayName: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="19050-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="19050-116">Execução isolada à atividade '%4', DisplayName: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="19050-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="19050-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="19050-117">Details</span></span>  
  
|<span data-ttu-id="19050-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="19050-118">Data Item Name</span></span>|<span data-ttu-id="19050-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="19050-119">Data Item Type</span></span>|<span data-ttu-id="19050-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="19050-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="19050-121">Atividade</span><span class="sxs-lookup"><span data-stu-id="19050-121">Activity</span></span>|<span data-ttu-id="19050-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="19050-122">xs:string</span></span>|<span data-ttu-id="19050-123">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="19050-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="19050-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="19050-124">DisplayName</span></span>|<span data-ttu-id="19050-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="19050-125">xs:string</span></span>|<span data-ttu-id="19050-126">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="19050-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="19050-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="19050-127">InstanceId</span></span>|<span data-ttu-id="19050-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="19050-128">xs:string</span></span>|<span data-ttu-id="19050-129">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="19050-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="19050-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="19050-130">IsolatedActivity</span></span>|<span data-ttu-id="19050-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="19050-131">xs:string</span></span>|<span data-ttu-id="19050-132">O nome do tipo de que a atividade isolada a transação está.</span><span class="sxs-lookup"><span data-stu-id="19050-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="19050-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="19050-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="19050-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="19050-134">xs:string</span></span>|<span data-ttu-id="19050-135">O nome para exibição de que a atividade isolada a transação está.</span><span class="sxs-lookup"><span data-stu-id="19050-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="19050-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="19050-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="19050-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="19050-137">xs:string</span></span>|<span data-ttu-id="19050-138">A identificação de instância de que a atividade isolada a transação está.</span><span class="sxs-lookup"><span data-stu-id="19050-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="19050-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="19050-139">AppDomain</span></span>|<span data-ttu-id="19050-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="19050-140">xs:string</span></span>|<span data-ttu-id="19050-141">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="19050-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
