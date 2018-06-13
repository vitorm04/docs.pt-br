---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509724"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="be982-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="be982-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="be982-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="be982-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="be982-104">ID</span><span class="sxs-lookup"><span data-stu-id="be982-104">ID</span></span>|<span data-ttu-id="be982-105">1029</span><span class="sxs-lookup"><span data-stu-id="be982-105">1029</span></span>|  
|<span data-ttu-id="be982-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="be982-106">Keywords</span></span>|<span data-ttu-id="be982-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="be982-107">WFRuntime</span></span>|  
|<span data-ttu-id="be982-108">Nível</span><span class="sxs-lookup"><span data-stu-id="be982-108">Level</span></span>|<span data-ttu-id="be982-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="be982-109">Verbose</span></span>|  
|<span data-ttu-id="be982-110">Canal</span><span class="sxs-lookup"><span data-stu-id="be982-110">Channel</span></span>|<span data-ttu-id="be982-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="be982-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="be982-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="be982-112">Description</span></span>  
 <span data-ttu-id="be982-113">Indica que um FaultWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="be982-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="be982-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="be982-114">Message</span></span>  
 <span data-ttu-id="be982-115">Um FaultWorkItem foi agendado para a atividade '%1', DisplayName: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="be982-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="be982-116">A exceção é propagada de atividade “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="be982-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="be982-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="be982-117">Details</span></span>  
  
|<span data-ttu-id="be982-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="be982-118">Data Item Name</span></span>|<span data-ttu-id="be982-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="be982-119">Data Item Type</span></span>|<span data-ttu-id="be982-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="be982-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="be982-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="be982-121">FaultActivity</span></span>|<span data-ttu-id="be982-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="be982-122">xs:string</span></span>|<span data-ttu-id="be982-123">O nome do tipo de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="be982-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="be982-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="be982-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="be982-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="be982-125">xs:string</span></span>|<span data-ttu-id="be982-126">O nome para exibição de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="be982-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="be982-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="be982-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="be982-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="be982-128">xs:string</span></span>|<span data-ttu-id="be982-129">A identificação de instância de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="be982-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="be982-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="be982-130">ExceptionActivity</span></span>|<span data-ttu-id="be982-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="be982-131">xs:string</span></span>|<span data-ttu-id="be982-132">O nome do tipo de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="be982-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="be982-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="be982-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="be982-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="be982-134">xs:string</span></span>|<span data-ttu-id="be982-135">O nome para exibição de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="be982-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="be982-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="be982-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="be982-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="be982-137">xs:string</span></span>|<span data-ttu-id="be982-138">A identificação de instância de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="be982-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="be982-139">Exceção</span><span class="sxs-lookup"><span data-stu-id="be982-139">Exception</span></span>|<span data-ttu-id="be982-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="be982-140">xs:string</span></span>|<span data-ttu-id="be982-141">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="be982-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="be982-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="be982-142">AppDomain</span></span>|<span data-ttu-id="be982-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="be982-143">xs:string</span></span>|<span data-ttu-id="be982-144">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="be982-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
