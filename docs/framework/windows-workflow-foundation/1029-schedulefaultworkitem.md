---
title: 1029 - ScheduleFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ba1ae69caff2e08da58e824d35341d3781ea8ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="fa12c-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="fa12c-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="fa12c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="fa12c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa12c-104">ID</span><span class="sxs-lookup"><span data-stu-id="fa12c-104">ID</span></span>|<span data-ttu-id="fa12c-105">1029</span><span class="sxs-lookup"><span data-stu-id="fa12c-105">1029</span></span>|  
|<span data-ttu-id="fa12c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="fa12c-106">Keywords</span></span>|<span data-ttu-id="fa12c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fa12c-107">WFRuntime</span></span>|  
|<span data-ttu-id="fa12c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="fa12c-108">Level</span></span>|<span data-ttu-id="fa12c-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="fa12c-109">Verbose</span></span>|  
|<span data-ttu-id="fa12c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="fa12c-110">Channel</span></span>|<span data-ttu-id="fa12c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="fa12c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fa12c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa12c-112">Description</span></span>  
 <span data-ttu-id="fa12c-113">Indica que um FaultWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="fa12c-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fa12c-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="fa12c-114">Message</span></span>  
 <span data-ttu-id="fa12c-115">Um FaultWorkItem foi agendado para a atividade '%1', DisplayName: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="fa12c-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="fa12c-116">A exceção é propagada de atividade “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="fa12c-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fa12c-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="fa12c-117">Details</span></span>  
  
|<span data-ttu-id="fa12c-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="fa12c-118">Data Item Name</span></span>|<span data-ttu-id="fa12c-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="fa12c-119">Data Item Type</span></span>|<span data-ttu-id="fa12c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa12c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fa12c-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="fa12c-121">FaultActivity</span></span>|<span data-ttu-id="fa12c-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="fa12c-122">xs:string</span></span>|<span data-ttu-id="fa12c-123">O nome do tipo de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="fa12c-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="fa12c-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="fa12c-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="fa12c-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="fa12c-125">xs:string</span></span>|<span data-ttu-id="fa12c-126">O nome para exibição de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="fa12c-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="fa12c-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="fa12c-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="fa12c-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="fa12c-128">xs:string</span></span>|<span data-ttu-id="fa12c-129">A identificação de instância de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="fa12c-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="fa12c-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="fa12c-130">ExceptionActivity</span></span>|<span data-ttu-id="fa12c-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="fa12c-131">xs:string</span></span>|<span data-ttu-id="fa12c-132">O nome do tipo de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="fa12c-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="fa12c-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="fa12c-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="fa12c-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="fa12c-134">xs:string</span></span>|<span data-ttu-id="fa12c-135">O nome para exibição de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="fa12c-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="fa12c-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="fa12c-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="fa12c-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="fa12c-137">xs:string</span></span>|<span data-ttu-id="fa12c-138">A identificação de instância de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="fa12c-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="fa12c-139">Exceção</span><span class="sxs-lookup"><span data-stu-id="fa12c-139">Exception</span></span>|<span data-ttu-id="fa12c-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="fa12c-140">xs:string</span></span>|<span data-ttu-id="fa12c-141">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="fa12c-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="fa12c-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fa12c-142">AppDomain</span></span>|<span data-ttu-id="fa12c-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="fa12c-143">xs:string</span></span>|<span data-ttu-id="fa12c-144">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fa12c-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
