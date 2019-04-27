---
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 3848d644e77041a62a52eb2eae5eeef286dfe334
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924313"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="e2b2a-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="e2b2a-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e2b2a-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e2b2a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e2b2a-104">ID</span><span class="sxs-lookup"><span data-stu-id="e2b2a-104">ID</span></span>|<span data-ttu-id="e2b2a-105">1030</span><span class="sxs-lookup"><span data-stu-id="e2b2a-105">1030</span></span>|  
|<span data-ttu-id="e2b2a-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="e2b2a-106">Keywords</span></span>|<span data-ttu-id="e2b2a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e2b2a-107">WFRuntime</span></span>|  
|<span data-ttu-id="e2b2a-108">Nível</span><span class="sxs-lookup"><span data-stu-id="e2b2a-108">Level</span></span>|<span data-ttu-id="e2b2a-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="e2b2a-109">Verbose</span></span>|  
|<span data-ttu-id="e2b2a-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e2b2a-110">Channel</span></span>|<span data-ttu-id="e2b2a-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="e2b2a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e2b2a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2b2a-112">Description</span></span>  
 <span data-ttu-id="e2b2a-113">Indica que um FaultWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="e2b2a-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e2b2a-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="e2b2a-114">Message</span></span>  
 <span data-ttu-id="e2b2a-115">Iniciar a execução de um FaultWorkItem para atividades "%1", DisplayName: "%2", InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="e2b2a-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="e2b2a-116">A exceção é propagada de atividade “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="e2b2a-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e2b2a-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e2b2a-117">Details</span></span>  
  
|<span data-ttu-id="e2b2a-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="e2b2a-118">Data Item Name</span></span>|<span data-ttu-id="e2b2a-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="e2b2a-119">Data Item Type</span></span>|<span data-ttu-id="e2b2a-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2b2a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e2b2a-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="e2b2a-121">FaultActivity</span></span>|<span data-ttu-id="e2b2a-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2b2a-122">xs:string</span></span>|<span data-ttu-id="e2b2a-123">O nome do tipo de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="e2b2a-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="e2b2a-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e2b2a-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="e2b2a-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2b2a-125">xs:string</span></span>|<span data-ttu-id="e2b2a-126">O nome para exibição de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="e2b2a-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="e2b2a-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e2b2a-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="e2b2a-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2b2a-128">xs:string</span></span>|<span data-ttu-id="e2b2a-129">A identificação de instância de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="e2b2a-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="e2b2a-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="e2b2a-130">ExceptionActivity</span></span>|<span data-ttu-id="e2b2a-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2b2a-131">xs:string</span></span>|<span data-ttu-id="e2b2a-132">O nome do tipo de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="e2b2a-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e2b2a-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e2b2a-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="e2b2a-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2b2a-134">xs:string</span></span>|<span data-ttu-id="e2b2a-135">O nome para exibição de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="e2b2a-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e2b2a-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e2b2a-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="e2b2a-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2b2a-137">xs:string</span></span>|<span data-ttu-id="e2b2a-138">A identificação de instância de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="e2b2a-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e2b2a-139">Exceção</span><span class="sxs-lookup"><span data-stu-id="e2b2a-139">Exception</span></span>|<span data-ttu-id="e2b2a-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2b2a-140">xs:string</span></span>|<span data-ttu-id="e2b2a-141">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="e2b2a-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="e2b2a-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e2b2a-142">AppDomain</span></span>|<span data-ttu-id="e2b2a-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2b2a-143">xs:string</span></span>|<span data-ttu-id="e2b2a-144">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e2b2a-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
