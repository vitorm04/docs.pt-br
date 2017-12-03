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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c2031a86a8d46a51b65e60a63a352c56b1a3a53
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="25e13-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="25e13-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="25e13-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="25e13-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="25e13-104">ID</span><span class="sxs-lookup"><span data-stu-id="25e13-104">ID</span></span>|<span data-ttu-id="25e13-105">1029</span><span class="sxs-lookup"><span data-stu-id="25e13-105">1029</span></span>|  
|<span data-ttu-id="25e13-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="25e13-106">Keywords</span></span>|<span data-ttu-id="25e13-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="25e13-107">WFRuntime</span></span>|  
|<span data-ttu-id="25e13-108">Nível</span><span class="sxs-lookup"><span data-stu-id="25e13-108">Level</span></span>|<span data-ttu-id="25e13-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="25e13-109">Verbose</span></span>|  
|<span data-ttu-id="25e13-110">Canal</span><span class="sxs-lookup"><span data-stu-id="25e13-110">Channel</span></span>|<span data-ttu-id="25e13-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="25e13-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="25e13-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="25e13-112">Description</span></span>  
 <span data-ttu-id="25e13-113">Indica que um FaultWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="25e13-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="25e13-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="25e13-114">Message</span></span>  
 <span data-ttu-id="25e13-115">Um FaultWorkItem foi agendado para a atividade '%1', DisplayName: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="25e13-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="25e13-116">A exceção é propagada de atividade “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="25e13-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="25e13-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="25e13-117">Details</span></span>  
  
|<span data-ttu-id="25e13-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="25e13-118">Data Item Name</span></span>|<span data-ttu-id="25e13-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="25e13-119">Data Item Type</span></span>|<span data-ttu-id="25e13-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="25e13-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="25e13-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="25e13-121">FaultActivity</span></span>|<span data-ttu-id="25e13-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="25e13-122">xs:string</span></span>|<span data-ttu-id="25e13-123">O nome do tipo de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="25e13-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="25e13-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="25e13-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="25e13-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="25e13-125">xs:string</span></span>|<span data-ttu-id="25e13-126">O nome para exibição de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="25e13-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="25e13-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="25e13-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="25e13-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="25e13-128">xs:string</span></span>|<span data-ttu-id="25e13-129">A identificação de instância de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="25e13-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="25e13-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="25e13-130">ExceptionActivity</span></span>|<span data-ttu-id="25e13-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="25e13-131">xs:string</span></span>|<span data-ttu-id="25e13-132">O nome do tipo de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="25e13-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="25e13-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="25e13-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="25e13-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="25e13-134">xs:string</span></span>|<span data-ttu-id="25e13-135">O nome para exibição de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="25e13-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="25e13-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="25e13-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="25e13-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="25e13-137">xs:string</span></span>|<span data-ttu-id="25e13-138">A identificação de instância de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="25e13-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="25e13-139">Exceção</span><span class="sxs-lookup"><span data-stu-id="25e13-139">Exception</span></span>|<span data-ttu-id="25e13-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="25e13-140">xs:string</span></span>|<span data-ttu-id="25e13-141">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="25e13-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="25e13-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="25e13-142">AppDomain</span></span>|<span data-ttu-id="25e13-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="25e13-143">xs:string</span></span>|<span data-ttu-id="25e13-144">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="25e13-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
