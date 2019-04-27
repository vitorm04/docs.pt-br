---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924651"
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="f13bd-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="f13bd-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="f13bd-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f13bd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f13bd-104">ID</span><span class="sxs-lookup"><span data-stu-id="f13bd-104">ID</span></span>|<span data-ttu-id="f13bd-105">1009</span><span class="sxs-lookup"><span data-stu-id="f13bd-105">1009</span></span>|  
|<span data-ttu-id="f13bd-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="f13bd-106">Keywords</span></span>|<span data-ttu-id="f13bd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f13bd-107">WFRuntime</span></span>|  
|<span data-ttu-id="f13bd-108">Nível</span><span class="sxs-lookup"><span data-stu-id="f13bd-108">Level</span></span>|<span data-ttu-id="f13bd-109">Informações</span><span class="sxs-lookup"><span data-stu-id="f13bd-109">Information</span></span>|  
|<span data-ttu-id="f13bd-110">Canal</span><span class="sxs-lookup"><span data-stu-id="f13bd-110">Channel</span></span>|<span data-ttu-id="f13bd-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="f13bd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f13bd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f13bd-112">Description</span></span>  
 <span data-ttu-id="f13bd-113">Indica que uma atividade está sendo agendada para a execução.</span><span class="sxs-lookup"><span data-stu-id="f13bd-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f13bd-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="f13bd-114">Message</span></span>  
 <span data-ttu-id="f13bd-115">Atividade pai “%1", DisplayName: “%2", InstanceId: “%3" agendaram a atividade filho “%4", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="f13bd-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f13bd-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f13bd-116">Details</span></span>  
  
|<span data-ttu-id="f13bd-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="f13bd-117">Data Item Name</span></span>|<span data-ttu-id="f13bd-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="f13bd-118">Data Item Type</span></span>|<span data-ttu-id="f13bd-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="f13bd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f13bd-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="f13bd-120">ParentActivity</span></span>|<span data-ttu-id="f13bd-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f13bd-121">xs:string</span></span>|<span data-ttu-id="f13bd-122">O nome do tipo de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="f13bd-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="f13bd-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="f13bd-123">ParentDisplayName</span></span>|<span data-ttu-id="f13bd-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f13bd-124">xs:string</span></span>|<span data-ttu-id="f13bd-125">O nome para exibição de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="f13bd-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="f13bd-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="f13bd-126">ParentInstanceId</span></span>|<span data-ttu-id="f13bd-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="f13bd-127">xs:string</span></span>|<span data-ttu-id="f13bd-128">A identificação de instância de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="f13bd-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="f13bd-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="f13bd-129">ChildActivity</span></span>|<span data-ttu-id="f13bd-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="f13bd-130">xs:string</span></span>|<span data-ttu-id="f13bd-131">O nome do tipo de atividade filho agendada.</span><span class="sxs-lookup"><span data-stu-id="f13bd-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="f13bd-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="f13bd-132">ChildDisplayName</span></span>|<span data-ttu-id="f13bd-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="f13bd-133">xs:string</span></span>|<span data-ttu-id="f13bd-134">O nome para exibição de atividade filho agendada.</span><span class="sxs-lookup"><span data-stu-id="f13bd-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="f13bd-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="f13bd-135">ChildInstanceId</span></span>|<span data-ttu-id="f13bd-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="f13bd-136">xs:string</span></span>|<span data-ttu-id="f13bd-137">A identificação de instância de atividade filho agendada.</span><span class="sxs-lookup"><span data-stu-id="f13bd-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="f13bd-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f13bd-138">AppDomain</span></span>|<span data-ttu-id="f13bd-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="f13bd-139">xs:string</span></span>|<span data-ttu-id="f13bd-140">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f13bd-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
