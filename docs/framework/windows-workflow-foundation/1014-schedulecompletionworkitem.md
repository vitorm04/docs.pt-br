---
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 50b00a49ea73dcbe09e8f4c4195cbce8c1cbf615
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982261"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="7c78b-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="7c78b-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="7c78b-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7c78b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7c78b-104">ID</span><span class="sxs-lookup"><span data-stu-id="7c78b-104">ID</span></span>|<span data-ttu-id="7c78b-105">1014</span><span class="sxs-lookup"><span data-stu-id="7c78b-105">1014</span></span>|  
|<span data-ttu-id="7c78b-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="7c78b-106">Keywords</span></span>|<span data-ttu-id="7c78b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7c78b-107">WFRuntime</span></span>|  
|<span data-ttu-id="7c78b-108">Nível</span><span class="sxs-lookup"><span data-stu-id="7c78b-108">Level</span></span>|<span data-ttu-id="7c78b-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="7c78b-109">Verbose</span></span>|  
|<span data-ttu-id="7c78b-110">Canal</span><span class="sxs-lookup"><span data-stu-id="7c78b-110">Channel</span></span>|<span data-ttu-id="7c78b-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="7c78b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7c78b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c78b-112">Description</span></span>  
 <span data-ttu-id="7c78b-113">Indica que um CompletionWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="7c78b-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7c78b-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="7c78b-114">Message</span></span>  
 <span data-ttu-id="7c78b-115">Um CompletionWorkItem foi agendado para atividades pai '%1', DisplayName: "%2", InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="7c78b-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="7c78b-116">Atividade counting “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="7c78b-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7c78b-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7c78b-117">Details</span></span>  
  
|<span data-ttu-id="7c78b-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="7c78b-118">Data Item Name</span></span>|<span data-ttu-id="7c78b-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="7c78b-119">Data Item Type</span></span>|<span data-ttu-id="7c78b-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c78b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7c78b-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="7c78b-121">ParentActivity</span></span>|<span data-ttu-id="7c78b-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="7c78b-122">xs:string</span></span>|<span data-ttu-id="7c78b-123">O nome do tipo de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="7c78b-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="7c78b-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="7c78b-124">ParentDisplayName</span></span>|<span data-ttu-id="7c78b-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="7c78b-125">xs:string</span></span>|<span data-ttu-id="7c78b-126">O nome para exibição de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="7c78b-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="7c78b-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="7c78b-127">ParentInstanceId</span></span>|<span data-ttu-id="7c78b-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="7c78b-128">xs:string</span></span>|<span data-ttu-id="7c78b-129">A identificação de instância de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="7c78b-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="7c78b-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="7c78b-130">CompletedActivity</span></span>|<span data-ttu-id="7c78b-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="7c78b-131">xs:string</span></span>|<span data-ttu-id="7c78b-132">O nome do tipo de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="7c78b-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="7c78b-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="7c78b-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="7c78b-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="7c78b-134">xs:string</span></span>|<span data-ttu-id="7c78b-135">O nome para exibição de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="7c78b-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="7c78b-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="7c78b-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="7c78b-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="7c78b-137">xs:string</span></span>|<span data-ttu-id="7c78b-138">A identificação de instância de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="7c78b-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="7c78b-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7c78b-139">AppDomain</span></span>|<span data-ttu-id="7c78b-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="7c78b-140">xs:string</span></span>|<span data-ttu-id="7c78b-141">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7c78b-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
