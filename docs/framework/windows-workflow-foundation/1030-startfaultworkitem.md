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
ms.openlocfilehash: c639de96bd72670b2641707e7283be2642801dbe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="c3c94-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="c3c94-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c3c94-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c3c94-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c3c94-104">ID</span><span class="sxs-lookup"><span data-stu-id="c3c94-104">ID</span></span>|<span data-ttu-id="c3c94-105">1030</span><span class="sxs-lookup"><span data-stu-id="c3c94-105">1030</span></span>|  
|<span data-ttu-id="c3c94-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="c3c94-106">Keywords</span></span>|<span data-ttu-id="c3c94-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c3c94-107">WFRuntime</span></span>|  
|<span data-ttu-id="c3c94-108">Nível</span><span class="sxs-lookup"><span data-stu-id="c3c94-108">Level</span></span>|<span data-ttu-id="c3c94-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="c3c94-109">Verbose</span></span>|  
|<span data-ttu-id="c3c94-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c3c94-110">Channel</span></span>|<span data-ttu-id="c3c94-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="c3c94-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c3c94-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3c94-112">Description</span></span>  
 <span data-ttu-id="c3c94-113">Indica que um FaultWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="c3c94-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c3c94-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c3c94-114">Message</span></span>  
 <span data-ttu-id="c3c94-115">Iniciando a execução de um FaultWorkItem para a atividade '%1', DisplayName: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="c3c94-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="c3c94-116">A exceção é propagada de atividade “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="c3c94-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c3c94-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c3c94-117">Details</span></span>  
  
|<span data-ttu-id="c3c94-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="c3c94-118">Data Item Name</span></span>|<span data-ttu-id="c3c94-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="c3c94-119">Data Item Type</span></span>|<span data-ttu-id="c3c94-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3c94-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c3c94-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="c3c94-121">FaultActivity</span></span>|<span data-ttu-id="c3c94-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3c94-122">xs:string</span></span>|<span data-ttu-id="c3c94-123">O nome do tipo de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="c3c94-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="c3c94-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="c3c94-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="c3c94-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3c94-125">xs:string</span></span>|<span data-ttu-id="c3c94-126">O nome para exibição de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="c3c94-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="c3c94-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="c3c94-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="c3c94-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3c94-128">xs:string</span></span>|<span data-ttu-id="c3c94-129">A identificação de instância de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="c3c94-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="c3c94-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="c3c94-130">ExceptionActivity</span></span>|<span data-ttu-id="c3c94-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3c94-131">xs:string</span></span>|<span data-ttu-id="c3c94-132">O nome do tipo de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="c3c94-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="c3c94-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="c3c94-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="c3c94-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3c94-134">xs:string</span></span>|<span data-ttu-id="c3c94-135">O nome para exibição de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="c3c94-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="c3c94-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="c3c94-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="c3c94-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3c94-137">xs:string</span></span>|<span data-ttu-id="c3c94-138">A identificação de instância de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="c3c94-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="c3c94-139">Exceção</span><span class="sxs-lookup"><span data-stu-id="c3c94-139">Exception</span></span>|<span data-ttu-id="c3c94-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3c94-140">xs:string</span></span>|<span data-ttu-id="c3c94-141">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="c3c94-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="c3c94-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c3c94-142">AppDomain</span></span>|<span data-ttu-id="c3c94-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3c94-143">xs:string</span></span>|<span data-ttu-id="c3c94-144">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c3c94-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
