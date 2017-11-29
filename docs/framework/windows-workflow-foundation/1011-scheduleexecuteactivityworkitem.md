---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 498752bfc896891a43a6a2e7a8245c508795c1ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="8d0f0-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="8d0f0-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="8d0f0-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8d0f0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8d0f0-104">ID</span><span class="sxs-lookup"><span data-stu-id="8d0f0-104">ID</span></span>|<span data-ttu-id="8d0f0-105">1011</span><span class="sxs-lookup"><span data-stu-id="8d0f0-105">1011</span></span>|  
|<span data-ttu-id="8d0f0-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="8d0f0-106">Keywords</span></span>|<span data-ttu-id="8d0f0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8d0f0-107">WFRuntime</span></span>|  
|<span data-ttu-id="8d0f0-108">Nível</span><span class="sxs-lookup"><span data-stu-id="8d0f0-108">Level</span></span>|<span data-ttu-id="8d0f0-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="8d0f0-109">Verbose</span></span>|  
|<span data-ttu-id="8d0f0-110">Canal</span><span class="sxs-lookup"><span data-stu-id="8d0f0-110">Channel</span></span>|<span data-ttu-id="8d0f0-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="8d0f0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8d0f0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d0f0-112">Description</span></span>  
 <span data-ttu-id="8d0f0-113">Indica que um ExecuteActivityWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="8d0f0-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8d0f0-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="8d0f0-114">Message</span></span>  
 <span data-ttu-id="8d0f0-115">Um ExecuteActivityWorkItem foi agendada para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="8d0f0-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8d0f0-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8d0f0-116">Details</span></span>  
  
|<span data-ttu-id="8d0f0-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="8d0f0-117">Data Item Name</span></span>|<span data-ttu-id="8d0f0-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="8d0f0-118">Data Item Type</span></span>|<span data-ttu-id="8d0f0-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d0f0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8d0f0-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="8d0f0-120">Activity</span></span>|<span data-ttu-id="8d0f0-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8d0f0-121">xs:string</span></span>|<span data-ttu-id="8d0f0-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="8d0f0-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="8d0f0-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8d0f0-123">DisplayName</span></span>|<span data-ttu-id="8d0f0-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8d0f0-124">xs:string</span></span>|<span data-ttu-id="8d0f0-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="8d0f0-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="8d0f0-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="8d0f0-126">InstanceId</span></span>|<span data-ttu-id="8d0f0-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="8d0f0-127">xs:string</span></span>|<span data-ttu-id="8d0f0-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="8d0f0-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="8d0f0-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8d0f0-129">AppDomain</span></span>|<span data-ttu-id="8d0f0-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="8d0f0-130">xs:string</span></span>|<span data-ttu-id="8d0f0-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8d0f0-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
