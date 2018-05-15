---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: 299d09b7c4db94a2e27378ba0cc3dfeb03734ab4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="0248b-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="0248b-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="0248b-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0248b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0248b-104">ID</span><span class="sxs-lookup"><span data-stu-id="0248b-104">ID</span></span>|<span data-ttu-id="0248b-105">1011</span><span class="sxs-lookup"><span data-stu-id="0248b-105">1011</span></span>|  
|<span data-ttu-id="0248b-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="0248b-106">Keywords</span></span>|<span data-ttu-id="0248b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0248b-107">WFRuntime</span></span>|  
|<span data-ttu-id="0248b-108">Nível</span><span class="sxs-lookup"><span data-stu-id="0248b-108">Level</span></span>|<span data-ttu-id="0248b-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="0248b-109">Verbose</span></span>|  
|<span data-ttu-id="0248b-110">Canal</span><span class="sxs-lookup"><span data-stu-id="0248b-110">Channel</span></span>|<span data-ttu-id="0248b-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="0248b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0248b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0248b-112">Description</span></span>  
 <span data-ttu-id="0248b-113">Indica que um ExecuteActivityWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="0248b-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0248b-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="0248b-114">Message</span></span>  
 <span data-ttu-id="0248b-115">Um ExecuteActivityWorkItem foi agendada para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="0248b-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0248b-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="0248b-116">Details</span></span>  
  
|<span data-ttu-id="0248b-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="0248b-117">Data Item Name</span></span>|<span data-ttu-id="0248b-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="0248b-118">Data Item Type</span></span>|<span data-ttu-id="0248b-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0248b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0248b-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="0248b-120">Activity</span></span>|<span data-ttu-id="0248b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="0248b-121">xs:string</span></span>|<span data-ttu-id="0248b-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="0248b-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="0248b-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="0248b-123">DisplayName</span></span>|<span data-ttu-id="0248b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="0248b-124">xs:string</span></span>|<span data-ttu-id="0248b-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="0248b-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="0248b-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="0248b-126">InstanceId</span></span>|<span data-ttu-id="0248b-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="0248b-127">xs:string</span></span>|<span data-ttu-id="0248b-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="0248b-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="0248b-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0248b-129">AppDomain</span></span>|<span data-ttu-id="0248b-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="0248b-130">xs:string</span></span>|<span data-ttu-id="0248b-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0248b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
