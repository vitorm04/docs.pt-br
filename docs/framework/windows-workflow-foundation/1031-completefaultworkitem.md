---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008792"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="3f9b2-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="3f9b2-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3f9b2-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3f9b2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3f9b2-104">ID</span><span class="sxs-lookup"><span data-stu-id="3f9b2-104">ID</span></span>|<span data-ttu-id="3f9b2-105">1031</span><span class="sxs-lookup"><span data-stu-id="3f9b2-105">1031</span></span>|  
|<span data-ttu-id="3f9b2-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="3f9b2-106">Keywords</span></span>|<span data-ttu-id="3f9b2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3f9b2-107">WFRuntime</span></span>|  
|<span data-ttu-id="3f9b2-108">Nível</span><span class="sxs-lookup"><span data-stu-id="3f9b2-108">Level</span></span>|<span data-ttu-id="3f9b2-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="3f9b2-109">Verbose</span></span>|  
|<span data-ttu-id="3f9b2-110">Canal</span><span class="sxs-lookup"><span data-stu-id="3f9b2-110">Channel</span></span>|<span data-ttu-id="3f9b2-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="3f9b2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3f9b2-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3f9b2-112">Description</span></span>  
 <span data-ttu-id="3f9b2-113">Indica que um FaultWorkItem terminado.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3f9b2-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="3f9b2-114">Message</span></span>  
 <span data-ttu-id="3f9b2-115">Um FaultWorkItem concluiu para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="3f9b2-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="3f9b2-116">A exceção é propagada de atividade “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="3f9b2-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3f9b2-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="3f9b2-117">Details</span></span>  
  
|<span data-ttu-id="3f9b2-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="3f9b2-118">Data Item Name</span></span>|<span data-ttu-id="3f9b2-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="3f9b2-119">Data Item Type</span></span>|<span data-ttu-id="3f9b2-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="3f9b2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3f9b2-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="3f9b2-121">FaultActivity</span></span>|<span data-ttu-id="3f9b2-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="3f9b2-122">xs:string</span></span>|<span data-ttu-id="3f9b2-123">O nome do tipo de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="3f9b2-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="3f9b2-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="3f9b2-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="3f9b2-125">xs:string</span></span>|<span data-ttu-id="3f9b2-126">O nome para exibição de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="3f9b2-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="3f9b2-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="3f9b2-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="3f9b2-128">xs:string</span></span>|<span data-ttu-id="3f9b2-129">A identificação de instância de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="3f9b2-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="3f9b2-130">ExceptionActivity</span></span>|<span data-ttu-id="3f9b2-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="3f9b2-131">xs:string</span></span>|<span data-ttu-id="3f9b2-132">O nome do tipo de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="3f9b2-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="3f9b2-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="3f9b2-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="3f9b2-134">xs:string</span></span>|<span data-ttu-id="3f9b2-135">O nome para exibição de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="3f9b2-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="3f9b2-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="3f9b2-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="3f9b2-137">xs:string</span></span>|<span data-ttu-id="3f9b2-138">A identificação de instância de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="3f9b2-139">Exceção</span><span class="sxs-lookup"><span data-stu-id="3f9b2-139">Exception</span></span>|<span data-ttu-id="3f9b2-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="3f9b2-140">xs:string</span></span>|<span data-ttu-id="3f9b2-141">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="3f9b2-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="3f9b2-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3f9b2-142">AppDomain</span></span>|<span data-ttu-id="3f9b2-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="3f9b2-143">xs:string</span></span>|<span data-ttu-id="3f9b2-144">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3f9b2-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
