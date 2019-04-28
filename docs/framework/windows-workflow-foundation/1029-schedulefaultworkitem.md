---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924352"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="3690e-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="3690e-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3690e-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3690e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3690e-104">ID</span><span class="sxs-lookup"><span data-stu-id="3690e-104">ID</span></span>|<span data-ttu-id="3690e-105">1029</span><span class="sxs-lookup"><span data-stu-id="3690e-105">1029</span></span>|  
|<span data-ttu-id="3690e-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="3690e-106">Keywords</span></span>|<span data-ttu-id="3690e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3690e-107">WFRuntime</span></span>|  
|<span data-ttu-id="3690e-108">Nível</span><span class="sxs-lookup"><span data-stu-id="3690e-108">Level</span></span>|<span data-ttu-id="3690e-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="3690e-109">Verbose</span></span>|  
|<span data-ttu-id="3690e-110">Canal</span><span class="sxs-lookup"><span data-stu-id="3690e-110">Channel</span></span>|<span data-ttu-id="3690e-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="3690e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3690e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3690e-112">Description</span></span>  
 <span data-ttu-id="3690e-113">Indica que um FaultWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="3690e-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3690e-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="3690e-114">Message</span></span>  
 <span data-ttu-id="3690e-115">Um FaultWorkItem foi agendado para atividades "%1', DisplayName:"%2", InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="3690e-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="3690e-116">A exceção é propagada de atividade “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="3690e-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3690e-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="3690e-117">Details</span></span>  
  
|<span data-ttu-id="3690e-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="3690e-118">Data Item Name</span></span>|<span data-ttu-id="3690e-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="3690e-119">Data Item Type</span></span>|<span data-ttu-id="3690e-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="3690e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3690e-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="3690e-121">FaultActivity</span></span>|<span data-ttu-id="3690e-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="3690e-122">xs:string</span></span>|<span data-ttu-id="3690e-123">O nome do tipo de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="3690e-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="3690e-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="3690e-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="3690e-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="3690e-125">xs:string</span></span>|<span data-ttu-id="3690e-126">O nome para exibição de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="3690e-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="3690e-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="3690e-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="3690e-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="3690e-128">xs:string</span></span>|<span data-ttu-id="3690e-129">A identificação de instância de atividade de falha.</span><span class="sxs-lookup"><span data-stu-id="3690e-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="3690e-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="3690e-130">ExceptionActivity</span></span>|<span data-ttu-id="3690e-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="3690e-131">xs:string</span></span>|<span data-ttu-id="3690e-132">O nome do tipo de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="3690e-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="3690e-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="3690e-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="3690e-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="3690e-134">xs:string</span></span>|<span data-ttu-id="3690e-135">O nome para exibição de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="3690e-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="3690e-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="3690e-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="3690e-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="3690e-137">xs:string</span></span>|<span data-ttu-id="3690e-138">A identificação de instância de atividade que apresentou a exceção.</span><span class="sxs-lookup"><span data-stu-id="3690e-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="3690e-139">Exceção</span><span class="sxs-lookup"><span data-stu-id="3690e-139">Exception</span></span>|<span data-ttu-id="3690e-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="3690e-140">xs:string</span></span>|<span data-ttu-id="3690e-141">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="3690e-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="3690e-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3690e-142">AppDomain</span></span>|<span data-ttu-id="3690e-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="3690e-143">xs:string</span></span>|<span data-ttu-id="3690e-144">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3690e-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
