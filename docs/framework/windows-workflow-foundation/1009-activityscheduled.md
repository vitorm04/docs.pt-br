---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="cf8d9-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="cf8d9-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="cf8d9-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="cf8d9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf8d9-104">ID</span><span class="sxs-lookup"><span data-stu-id="cf8d9-104">ID</span></span>|<span data-ttu-id="cf8d9-105">1009</span><span class="sxs-lookup"><span data-stu-id="cf8d9-105">1009</span></span>|  
|<span data-ttu-id="cf8d9-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="cf8d9-106">Keywords</span></span>|<span data-ttu-id="cf8d9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cf8d9-107">WFRuntime</span></span>|  
|<span data-ttu-id="cf8d9-108">Nível</span><span class="sxs-lookup"><span data-stu-id="cf8d9-108">Level</span></span>|<span data-ttu-id="cf8d9-109">Informações</span><span class="sxs-lookup"><span data-stu-id="cf8d9-109">Information</span></span>|  
|<span data-ttu-id="cf8d9-110">Canal</span><span class="sxs-lookup"><span data-stu-id="cf8d9-110">Channel</span></span>|<span data-ttu-id="cf8d9-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="cf8d9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cf8d9-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf8d9-112">Description</span></span>  
 <span data-ttu-id="cf8d9-113">Indica que uma atividade está sendo agendada para a execução.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cf8d9-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="cf8d9-114">Message</span></span>  
 <span data-ttu-id="cf8d9-115">Atividade pai “%1", DisplayName: “%2", InstanceId: “%3" agendaram a atividade filho “%4", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="cf8d9-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cf8d9-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="cf8d9-116">Details</span></span>  
  
|<span data-ttu-id="cf8d9-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="cf8d9-117">Data Item Name</span></span>|<span data-ttu-id="cf8d9-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="cf8d9-118">Data Item Type</span></span>|<span data-ttu-id="cf8d9-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf8d9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cf8d9-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="cf8d9-120">ParentActivity</span></span>|<span data-ttu-id="cf8d9-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="cf8d9-121">xs:string</span></span>|<span data-ttu-id="cf8d9-122">O nome do tipo de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="cf8d9-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="cf8d9-123">ParentDisplayName</span></span>|<span data-ttu-id="cf8d9-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="cf8d9-124">xs:string</span></span>|<span data-ttu-id="cf8d9-125">O nome para exibição de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="cf8d9-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="cf8d9-126">ParentInstanceId</span></span>|<span data-ttu-id="cf8d9-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="cf8d9-127">xs:string</span></span>|<span data-ttu-id="cf8d9-128">A identificação de instância de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="cf8d9-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="cf8d9-129">ChildActivity</span></span>|<span data-ttu-id="cf8d9-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="cf8d9-130">xs:string</span></span>|<span data-ttu-id="cf8d9-131">O nome do tipo de atividade filho agendada.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="cf8d9-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="cf8d9-132">ChildDisplayName</span></span>|<span data-ttu-id="cf8d9-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="cf8d9-133">xs:string</span></span>|<span data-ttu-id="cf8d9-134">O nome para exibição de atividade filho agendada.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="cf8d9-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="cf8d9-135">ChildInstanceId</span></span>|<span data-ttu-id="cf8d9-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="cf8d9-136">xs:string</span></span>|<span data-ttu-id="cf8d9-137">A identificação de instância de atividade filho agendada.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="cf8d9-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cf8d9-138">AppDomain</span></span>|<span data-ttu-id="cf8d9-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="cf8d9-139">xs:string</span></span>|<span data-ttu-id="cf8d9-140">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="cf8d9-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
