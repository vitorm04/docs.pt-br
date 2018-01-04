---
title: 116 - WorkflowInstanceSuspendedRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38232c03-6139-4494-a020-79bc83eb9dce
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59bd66cbfee7c56045f42d6d9fda254408ae63db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="116---workflowinstancesuspendedrecordwithid"></a><span data-ttu-id="64d82-102">116 - WorkflowInstanceSuspendedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="64d82-102">116 - WorkflowInstanceSuspendedRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="64d82-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="64d82-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="64d82-104">ID</span><span class="sxs-lookup"><span data-stu-id="64d82-104">ID</span></span>|<span data-ttu-id="64d82-105">116</span><span class="sxs-lookup"><span data-stu-id="64d82-105">116</span></span>|  
|<span data-ttu-id="64d82-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="64d82-106">Keywords</span></span>|<span data-ttu-id="64d82-107">HealthMonitoring, WFTracking</span><span class="sxs-lookup"><span data-stu-id="64d82-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="64d82-108">Nível</span><span class="sxs-lookup"><span data-stu-id="64d82-108">Level</span></span>|<span data-ttu-id="64d82-109">Informações</span><span class="sxs-lookup"><span data-stu-id="64d82-109">Information</span></span>|  
|<span data-ttu-id="64d82-110">Canal</span><span class="sxs-lookup"><span data-stu-id="64d82-110">Channel</span></span>|<span data-ttu-id="64d82-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="64d82-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="64d82-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="64d82-112">Description</span></span>  
 <span data-ttu-id="64d82-113">Este evento é emitido pelo participante de rastreamento de ETW quando uma instância de fluxo de trabalho se chama o registro de WorkflowInstanceSuspended.</span><span class="sxs-lookup"><span data-stu-id="64d82-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceSuspended Record.</span></span>  
  
## <a name="message"></a><span data-ttu-id="64d82-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="64d82-114">Message</span></span>  
 <span data-ttu-id="64d82-115">TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, razão = %5, anotações = %6 ProfileName, =, %7 WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="64d82-115">TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="64d82-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="64d82-116">Details</span></span>  
  
|<span data-ttu-id="64d82-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="64d82-117">Data Item Name</span></span>|<span data-ttu-id="64d82-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="64d82-118">Data Item Type</span></span>|<span data-ttu-id="64d82-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="64d82-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="64d82-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="64d82-120">InstanceId</span></span>|<span data-ttu-id="64d82-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="64d82-121">xs:GUID</span></span>|<span data-ttu-id="64d82-122">A identificação de instância para o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="64d82-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="64d82-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="64d82-123">RecordNumber</span></span>|<span data-ttu-id="64d82-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="64d82-124">xs:long</span></span>|<span data-ttu-id="64d82-125">O número de sequência do registro emitido</span><span class="sxs-lookup"><span data-stu-id="64d82-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="64d82-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="64d82-126">EventTime</span></span>|<span data-ttu-id="64d82-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="64d82-127">xs:dateTime</span></span>|<span data-ttu-id="64d82-128">A hora UTC quando o evento foi emitido</span><span class="sxs-lookup"><span data-stu-id="64d82-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="64d82-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="64d82-129">ActivityDefinitionId</span></span>|<span data-ttu-id="64d82-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="64d82-130">xs:string</span></span>|<span data-ttu-id="64d82-131">O nome da atividade raiz no fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="64d82-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="64d82-132">Estado</span><span class="sxs-lookup"><span data-stu-id="64d82-132">State</span></span>|<span data-ttu-id="64d82-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="64d82-133">xs:string</span></span>|<span data-ttu-id="64d82-134">O estado atual de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="64d82-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="64d82-135">Anotações</span><span class="sxs-lookup"><span data-stu-id="64d82-135">Annotations</span></span>|<span data-ttu-id="64d82-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="64d82-136">xs:string</span></span>|<span data-ttu-id="64d82-137">As anotações que foram adicionadas a este evento.</span><span class="sxs-lookup"><span data-stu-id="64d82-137">The annotations that were added to this event.</span></span> <span data-ttu-id="64d82-138">Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "annotationName" type="System.String" > annotationValue\</item > \< /itens >.</span><span class="sxs-lookup"><span data-stu-id="64d82-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="64d82-139">Se nenhuma anotação é especificada, em seguida, a cadeia de caracteres contém \<itens / >.</span><span class="sxs-lookup"><span data-stu-id="64d82-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="64d82-140">O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW.</span><span class="sxs-lookup"><span data-stu-id="64d82-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="64d82-141">Se o tamanho do evento excede os limites ETW, o evento é truncado descartando as anotações e substituindo o valor anotação com \<itens >...  \< /itens >.</span><span class="sxs-lookup"><span data-stu-id="64d82-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="64d82-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="64d82-142">ProfileName</span></span>|<span data-ttu-id="64d82-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="64d82-143">xs:string</span></span>|<span data-ttu-id="64d82-144">O nome ou o perfil de rastreamento que levam a este evento que está sendo emitido</span><span class="sxs-lookup"><span data-stu-id="64d82-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="64d82-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="64d82-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="64d82-146">xs:string</span><span class="sxs-lookup"><span data-stu-id="64d82-146">xs:string</span></span>|<span data-ttu-id="64d82-147">A identificação da definição de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="64d82-147">The workflow definition id</span></span>|  
|<span data-ttu-id="64d82-148">AppDomain</span><span class="sxs-lookup"><span data-stu-id="64d82-148">AppDomain</span></span>|<span data-ttu-id="64d82-149">xs:string</span><span class="sxs-lookup"><span data-stu-id="64d82-149">xs:string</span></span>|<span data-ttu-id="64d82-150">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="64d82-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
