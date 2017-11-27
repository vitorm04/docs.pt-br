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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b25dbd5ced96b8e9ca3ef51e4de841a6238d2cbc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="e2ac7-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="e2ac7-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e2ac7-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e2ac7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e2ac7-104">ID</span><span class="sxs-lookup"><span data-stu-id="e2ac7-104">ID</span></span>|<span data-ttu-id="e2ac7-105">1030</span><span class="sxs-lookup"><span data-stu-id="e2ac7-105">1030</span></span>|  
|<span data-ttu-id="e2ac7-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="e2ac7-106">Keywords</span></span>|<span data-ttu-id="e2ac7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e2ac7-107">WFRuntime</span></span>|  
|<span data-ttu-id="e2ac7-108">Nível</span><span class="sxs-lookup"><span data-stu-id="e2ac7-108">Level</span></span>|<span data-ttu-id="e2ac7-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="e2ac7-109">Verbose</span></span>|  
|<span data-ttu-id="e2ac7-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e2ac7-110">Channel</span></span>|<span data-ttu-id="e2ac7-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="e2ac7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e2ac7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2ac7-112">Description</span></span>  
 <span data-ttu-id="e2ac7-113">Indica que um FaultWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e2ac7-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="e2ac7-114">Message</span></span>  
 <span data-ttu-id="e2ac7-115">Iniciando a execução de um FaultWorkItem para a atividade '%1', DisplayName: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="e2ac7-116">A exceção é propagada de atividade “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="e2ac7-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e2ac7-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e2ac7-117">Details</span></span>  
  
|<span data-ttu-id="e2ac7-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="e2ac7-118">Data Item Name</span></span>|<span data-ttu-id="e2ac7-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="e2ac7-119">Data Item Type</span></span>|<span data-ttu-id="e2ac7-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2ac7-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e2ac7-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="e2ac7-121">FaultActivity</span></span>|<span data-ttu-id="e2ac7-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2ac7-122">xs:string</span></span>|<span data-ttu-id="e2ac7-123">O nome do tipo de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="e2ac7-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e2ac7-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="e2ac7-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2ac7-125">xs:string</span></span>|<span data-ttu-id="e2ac7-126">O nome para exibição de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="e2ac7-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e2ac7-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="e2ac7-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2ac7-128">xs:string</span></span>|<span data-ttu-id="e2ac7-129">A identificação de instância de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="e2ac7-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="e2ac7-130">ExceptionActivity</span></span>|<span data-ttu-id="e2ac7-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2ac7-131">xs:string</span></span>|<span data-ttu-id="e2ac7-132">O nome do tipo de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e2ac7-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e2ac7-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="e2ac7-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2ac7-134">xs:string</span></span>|<span data-ttu-id="e2ac7-135">O nome para exibição de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e2ac7-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e2ac7-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="e2ac7-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2ac7-137">xs:string</span></span>|<span data-ttu-id="e2ac7-138">A identificação de instância de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e2ac7-139">Exceção</span><span class="sxs-lookup"><span data-stu-id="e2ac7-139">Exception</span></span>|<span data-ttu-id="e2ac7-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2ac7-140">xs:string</span></span>|<span data-ttu-id="e2ac7-141">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="e2ac7-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="e2ac7-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e2ac7-142">AppDomain</span></span>|<span data-ttu-id="e2ac7-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2ac7-143">xs:string</span></span>|<span data-ttu-id="e2ac7-144">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
