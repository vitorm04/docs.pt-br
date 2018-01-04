---
title: 117 - WorkflowInstanceTerminatedRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e68539d0-5338-468a-9f75-7e5b09d39a3c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3fd8ece3245b99a5d976058135492e8503dd1c8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="117---workflowinstanceterminatedrecordwithid"></a><span data-ttu-id="8e422-102">117 - WorkflowInstanceTerminatedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="8e422-102">117 - WorkflowInstanceTerminatedRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="8e422-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8e422-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8e422-104">ID</span><span class="sxs-lookup"><span data-stu-id="8e422-104">ID</span></span>|<span data-ttu-id="8e422-105">117</span><span class="sxs-lookup"><span data-stu-id="8e422-105">117</span></span>|  
|<span data-ttu-id="8e422-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="8e422-106">Keywords</span></span>|<span data-ttu-id="8e422-107">HealthMonitoring, WFTracking</span><span class="sxs-lookup"><span data-stu-id="8e422-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="8e422-108">Nível</span><span class="sxs-lookup"><span data-stu-id="8e422-108">Level</span></span>|<span data-ttu-id="8e422-109">Erro</span><span class="sxs-lookup"><span data-stu-id="8e422-109">Error</span></span>|  
|<span data-ttu-id="8e422-110">Canal</span><span class="sxs-lookup"><span data-stu-id="8e422-110">Channel</span></span>|<span data-ttu-id="8e422-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="8e422-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8e422-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e422-112">Description</span></span>  
 <span data-ttu-id="8e422-113">Este evento é emitido pelo participante de rastreamento de ETW quando uma instância de fluxo de trabalho se emite WorkflowInstanceTerminatedRecord.</span><span class="sxs-lookup"><span data-stu-id="8e422-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceTerminatedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8e422-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="8e422-114">Message</span></span>  
 <span data-ttu-id="8e422-115">TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, motivo = %5, anotações = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="8e422-115">TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5,  Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="8e422-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8e422-116">Details</span></span>  
  
|<span data-ttu-id="8e422-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="8e422-117">Data Item Name</span></span>|<span data-ttu-id="8e422-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="8e422-118">Data Item Type</span></span>|<span data-ttu-id="8e422-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e422-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8e422-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="8e422-120">InstanceId</span></span>|<span data-ttu-id="8e422-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="8e422-121">xs:GUID</span></span>|<span data-ttu-id="8e422-122">A identificação de instância para o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8e422-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="8e422-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="8e422-123">RecordNumber</span></span>|<span data-ttu-id="8e422-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="8e422-124">xs:long</span></span>|<span data-ttu-id="8e422-125">O número de sequência do registro emitido</span><span class="sxs-lookup"><span data-stu-id="8e422-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="8e422-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="8e422-126">EventTime</span></span>|<span data-ttu-id="8e422-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="8e422-127">xs:dateTime</span></span>|<span data-ttu-id="8e422-128">A hora UTC quando o evento foi emitido</span><span class="sxs-lookup"><span data-stu-id="8e422-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="8e422-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="8e422-129">ActivityDefinitionId</span></span>|<span data-ttu-id="8e422-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e422-130">xs:string</span></span>|<span data-ttu-id="8e422-131">O nome da atividade raiz no fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8e422-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="8e422-132">Estado</span><span class="sxs-lookup"><span data-stu-id="8e422-132">State</span></span>|<span data-ttu-id="8e422-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e422-133">xs:string</span></span>|<span data-ttu-id="8e422-134">O estado atual de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8e422-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="8e422-135">Anotações</span><span class="sxs-lookup"><span data-stu-id="8e422-135">Annotations</span></span>|<span data-ttu-id="8e422-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e422-136">xs:string</span></span>|<span data-ttu-id="8e422-137">As anotações que foram adicionadas a este evento.</span><span class="sxs-lookup"><span data-stu-id="8e422-137">The annotations that were added to this event.</span></span> <span data-ttu-id="8e422-138">Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "annotationName" type="System.String" > annotationValue\</item > \< /itens >.</span><span class="sxs-lookup"><span data-stu-id="8e422-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="8e422-139">Se nenhuma anotação é especificada, em seguida, a cadeia de caracteres contém \<itens / >.</span><span class="sxs-lookup"><span data-stu-id="8e422-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="8e422-140">O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW.</span><span class="sxs-lookup"><span data-stu-id="8e422-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="8e422-141">Se o tamanho do evento excede os limites ETW, o evento é truncado descartando as anotações e substituindo o valor anotação com \<itens >...  \< /itens >.</span><span class="sxs-lookup"><span data-stu-id="8e422-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="8e422-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="8e422-142">ProfileName</span></span>|<span data-ttu-id="8e422-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e422-143">xs:string</span></span>|<span data-ttu-id="8e422-144">O nome ou o perfil de rastreamento que levam a este evento que está sendo emitido</span><span class="sxs-lookup"><span data-stu-id="8e422-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="8e422-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="8e422-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="8e422-146">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e422-146">xs:string</span></span>|<span data-ttu-id="8e422-147">A identificação da definição de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8e422-147">The workflow definition id</span></span>|  
|<span data-ttu-id="8e422-148">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8e422-148">AppDomain</span></span>|<span data-ttu-id="8e422-149">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e422-149">xs:string</span></span>|<span data-ttu-id="8e422-150">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8e422-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
