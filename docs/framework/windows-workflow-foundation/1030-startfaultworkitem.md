---
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 3848d644e77041a62a52eb2eae5eeef286dfe334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509674"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="5956e-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="5956e-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="5956e-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5956e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5956e-104">ID</span><span class="sxs-lookup"><span data-stu-id="5956e-104">ID</span></span>|<span data-ttu-id="5956e-105">1030</span><span class="sxs-lookup"><span data-stu-id="5956e-105">1030</span></span>|  
|<span data-ttu-id="5956e-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="5956e-106">Keywords</span></span>|<span data-ttu-id="5956e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5956e-107">WFRuntime</span></span>|  
|<span data-ttu-id="5956e-108">Nível</span><span class="sxs-lookup"><span data-stu-id="5956e-108">Level</span></span>|<span data-ttu-id="5956e-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="5956e-109">Verbose</span></span>|  
|<span data-ttu-id="5956e-110">Canal</span><span class="sxs-lookup"><span data-stu-id="5956e-110">Channel</span></span>|<span data-ttu-id="5956e-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="5956e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5956e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5956e-112">Description</span></span>  
 <span data-ttu-id="5956e-113">Indica que um FaultWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="5956e-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5956e-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="5956e-114">Message</span></span>  
 <span data-ttu-id="5956e-115">Iniciando a execução de um FaultWorkItem para a atividade '%1', DisplayName: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="5956e-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="5956e-116">A exceção é propagada de atividade “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="5956e-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5956e-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5956e-117">Details</span></span>  
  
|<span data-ttu-id="5956e-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="5956e-118">Data Item Name</span></span>|<span data-ttu-id="5956e-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="5956e-119">Data Item Type</span></span>|<span data-ttu-id="5956e-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="5956e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5956e-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="5956e-121">FaultActivity</span></span>|<span data-ttu-id="5956e-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="5956e-122">xs:string</span></span>|<span data-ttu-id="5956e-123">O nome do tipo de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="5956e-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="5956e-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="5956e-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="5956e-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="5956e-125">xs:string</span></span>|<span data-ttu-id="5956e-126">O nome para exibição de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="5956e-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="5956e-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="5956e-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="5956e-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="5956e-128">xs:string</span></span>|<span data-ttu-id="5956e-129">A identificação de instância de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="5956e-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="5956e-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="5956e-130">ExceptionActivity</span></span>|<span data-ttu-id="5956e-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="5956e-131">xs:string</span></span>|<span data-ttu-id="5956e-132">O nome do tipo de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="5956e-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="5956e-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="5956e-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="5956e-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="5956e-134">xs:string</span></span>|<span data-ttu-id="5956e-135">O nome para exibição de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="5956e-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="5956e-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="5956e-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="5956e-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="5956e-137">xs:string</span></span>|<span data-ttu-id="5956e-138">A identificação de instância de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="5956e-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="5956e-139">Exceção</span><span class="sxs-lookup"><span data-stu-id="5956e-139">Exception</span></span>|<span data-ttu-id="5956e-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="5956e-140">xs:string</span></span>|<span data-ttu-id="5956e-141">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="5956e-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="5956e-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5956e-142">AppDomain</span></span>|<span data-ttu-id="5956e-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="5956e-143">xs:string</span></span>|<span data-ttu-id="5956e-144">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5956e-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
