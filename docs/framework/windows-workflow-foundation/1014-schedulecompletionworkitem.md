---
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 50b00a49ea73dcbe09e8f4c4195cbce8c1cbf615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510361"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="d8e52-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="d8e52-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="d8e52-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d8e52-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d8e52-104">ID</span><span class="sxs-lookup"><span data-stu-id="d8e52-104">ID</span></span>|<span data-ttu-id="d8e52-105">1014</span><span class="sxs-lookup"><span data-stu-id="d8e52-105">1014</span></span>|  
|<span data-ttu-id="d8e52-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="d8e52-106">Keywords</span></span>|<span data-ttu-id="d8e52-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d8e52-107">WFRuntime</span></span>|  
|<span data-ttu-id="d8e52-108">Nível</span><span class="sxs-lookup"><span data-stu-id="d8e52-108">Level</span></span>|<span data-ttu-id="d8e52-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="d8e52-109">Verbose</span></span>|  
|<span data-ttu-id="d8e52-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d8e52-110">Channel</span></span>|<span data-ttu-id="d8e52-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="d8e52-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d8e52-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8e52-112">Description</span></span>  
 <span data-ttu-id="d8e52-113">Indica que um CompletionWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="d8e52-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d8e52-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d8e52-114">Message</span></span>  
 <span data-ttu-id="d8e52-115">Um CompletionWorkItem foi agendado para a atividade pai '%1', DisplayName: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="d8e52-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="d8e52-116">Atividade counting “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="d8e52-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d8e52-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d8e52-117">Details</span></span>  
  
|<span data-ttu-id="d8e52-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="d8e52-118">Data Item Name</span></span>|<span data-ttu-id="d8e52-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="d8e52-119">Data Item Type</span></span>|<span data-ttu-id="d8e52-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8e52-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d8e52-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="d8e52-121">ParentActivity</span></span>|<span data-ttu-id="d8e52-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="d8e52-122">xs:string</span></span>|<span data-ttu-id="d8e52-123">O nome do tipo de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="d8e52-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="d8e52-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="d8e52-124">ParentDisplayName</span></span>|<span data-ttu-id="d8e52-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="d8e52-125">xs:string</span></span>|<span data-ttu-id="d8e52-126">O nome para exibição de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="d8e52-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="d8e52-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="d8e52-127">ParentInstanceId</span></span>|<span data-ttu-id="d8e52-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="d8e52-128">xs:string</span></span>|<span data-ttu-id="d8e52-129">A identificação de instância de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="d8e52-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="d8e52-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="d8e52-130">CompletedActivity</span></span>|<span data-ttu-id="d8e52-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="d8e52-131">xs:string</span></span>|<span data-ttu-id="d8e52-132">O nome do tipo de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="d8e52-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="d8e52-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="d8e52-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="d8e52-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="d8e52-134">xs:string</span></span>|<span data-ttu-id="d8e52-135">O nome para exibição de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="d8e52-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="d8e52-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="d8e52-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="d8e52-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="d8e52-137">xs:string</span></span>|<span data-ttu-id="d8e52-138">A identificação de instância de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="d8e52-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="d8e52-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d8e52-139">AppDomain</span></span>|<span data-ttu-id="d8e52-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="d8e52-140">xs:string</span></span>|<span data-ttu-id="d8e52-141">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d8e52-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
