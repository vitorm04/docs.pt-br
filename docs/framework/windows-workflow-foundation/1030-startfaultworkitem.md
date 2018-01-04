---
title: 1030 - StartFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 436a0323fcf4498a1d707f7af9bd8204885fd645
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="e8452-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="e8452-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e8452-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e8452-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e8452-104">ID</span><span class="sxs-lookup"><span data-stu-id="e8452-104">ID</span></span>|<span data-ttu-id="e8452-105">1030</span><span class="sxs-lookup"><span data-stu-id="e8452-105">1030</span></span>|  
|<span data-ttu-id="e8452-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="e8452-106">Keywords</span></span>|<span data-ttu-id="e8452-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e8452-107">WFRuntime</span></span>|  
|<span data-ttu-id="e8452-108">Nível</span><span class="sxs-lookup"><span data-stu-id="e8452-108">Level</span></span>|<span data-ttu-id="e8452-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="e8452-109">Verbose</span></span>|  
|<span data-ttu-id="e8452-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e8452-110">Channel</span></span>|<span data-ttu-id="e8452-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="e8452-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e8452-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8452-112">Description</span></span>  
 <span data-ttu-id="e8452-113">Indica que um FaultWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="e8452-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e8452-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="e8452-114">Message</span></span>  
 <span data-ttu-id="e8452-115">Iniciando a execução de um FaultWorkItem para a atividade '%1', DisplayName: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="e8452-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="e8452-116">A exceção é propagada de atividade “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="e8452-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e8452-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e8452-117">Details</span></span>  
  
|<span data-ttu-id="e8452-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="e8452-118">Data Item Name</span></span>|<span data-ttu-id="e8452-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="e8452-119">Data Item Type</span></span>|<span data-ttu-id="e8452-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8452-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e8452-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="e8452-121">FaultActivity</span></span>|<span data-ttu-id="e8452-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e8452-122">xs:string</span></span>|<span data-ttu-id="e8452-123">O nome do tipo de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="e8452-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="e8452-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e8452-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="e8452-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e8452-125">xs:string</span></span>|<span data-ttu-id="e8452-126">O nome para exibição de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="e8452-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="e8452-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e8452-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="e8452-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="e8452-128">xs:string</span></span>|<span data-ttu-id="e8452-129">A identificação de instância de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="e8452-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="e8452-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="e8452-130">ExceptionActivity</span></span>|<span data-ttu-id="e8452-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="e8452-131">xs:string</span></span>|<span data-ttu-id="e8452-132">O nome do tipo de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="e8452-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e8452-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e8452-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="e8452-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="e8452-134">xs:string</span></span>|<span data-ttu-id="e8452-135">O nome para exibição de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="e8452-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e8452-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e8452-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="e8452-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="e8452-137">xs:string</span></span>|<span data-ttu-id="e8452-138">A identificação de instância de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="e8452-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e8452-139">Exceção</span><span class="sxs-lookup"><span data-stu-id="e8452-139">Exception</span></span>|<span data-ttu-id="e8452-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="e8452-140">xs:string</span></span>|<span data-ttu-id="e8452-141">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="e8452-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="e8452-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e8452-142">AppDomain</span></span>|<span data-ttu-id="e8452-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="e8452-143">xs:string</span></span>|<span data-ttu-id="e8452-144">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e8452-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
