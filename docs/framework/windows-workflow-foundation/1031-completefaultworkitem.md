---
title: 1031 - CompleteFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 260647b56d945600afea5609f06d36385fa66014
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="d68c4-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="d68c4-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="d68c4-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d68c4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d68c4-104">ID</span><span class="sxs-lookup"><span data-stu-id="d68c4-104">ID</span></span>|<span data-ttu-id="d68c4-105">1031</span><span class="sxs-lookup"><span data-stu-id="d68c4-105">1031</span></span>|  
|<span data-ttu-id="d68c4-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="d68c4-106">Keywords</span></span>|<span data-ttu-id="d68c4-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d68c4-107">WFRuntime</span></span>|  
|<span data-ttu-id="d68c4-108">Nível</span><span class="sxs-lookup"><span data-stu-id="d68c4-108">Level</span></span>|<span data-ttu-id="d68c4-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="d68c4-109">Verbose</span></span>|  
|<span data-ttu-id="d68c4-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d68c4-110">Channel</span></span>|<span data-ttu-id="d68c4-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="d68c4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d68c4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d68c4-112">Description</span></span>  
 <span data-ttu-id="d68c4-113">Indica que um FaultWorkItem terminado.</span><span class="sxs-lookup"><span data-stu-id="d68c4-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d68c4-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d68c4-114">Message</span></span>  
 <span data-ttu-id="d68c4-115">Um FaultWorkItem concluiu para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="d68c4-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="d68c4-116">A exceção é propagada de atividade “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="d68c4-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d68c4-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d68c4-117">Details</span></span>  
  
|<span data-ttu-id="d68c4-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="d68c4-118">Data Item Name</span></span>|<span data-ttu-id="d68c4-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="d68c4-119">Data Item Type</span></span>|<span data-ttu-id="d68c4-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="d68c4-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d68c4-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="d68c4-121">FaultActivity</span></span>|<span data-ttu-id="d68c4-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="d68c4-122">xs:string</span></span>|<span data-ttu-id="d68c4-123">O nome do tipo de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="d68c4-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="d68c4-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="d68c4-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="d68c4-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="d68c4-125">xs:string</span></span>|<span data-ttu-id="d68c4-126">O nome para exibição de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="d68c4-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="d68c4-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="d68c4-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="d68c4-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="d68c4-128">xs:string</span></span>|<span data-ttu-id="d68c4-129">A identificação de instância de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="d68c4-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="d68c4-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="d68c4-130">ExceptionActivity</span></span>|<span data-ttu-id="d68c4-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="d68c4-131">xs:string</span></span>|<span data-ttu-id="d68c4-132">O nome do tipo de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="d68c4-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="d68c4-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="d68c4-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="d68c4-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="d68c4-134">xs:string</span></span>|<span data-ttu-id="d68c4-135">O nome para exibição de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="d68c4-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="d68c4-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="d68c4-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="d68c4-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="d68c4-137">xs:string</span></span>|<span data-ttu-id="d68c4-138">A identificação de instância de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="d68c4-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="d68c4-139">Exceção</span><span class="sxs-lookup"><span data-stu-id="d68c4-139">Exception</span></span>|<span data-ttu-id="d68c4-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="d68c4-140">xs:string</span></span>|<span data-ttu-id="d68c4-141">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="d68c4-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="d68c4-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d68c4-142">AppDomain</span></span>|<span data-ttu-id="d68c4-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="d68c4-143">xs:string</span></span>|<span data-ttu-id="d68c4-144">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d68c4-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
