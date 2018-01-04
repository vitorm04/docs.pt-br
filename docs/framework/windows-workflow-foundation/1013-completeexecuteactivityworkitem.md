---
title: 1013 - CompleteExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0dc72081d2e9b89a9979651bb02b6c06448e30e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="1c70f-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="1c70f-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1c70f-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1c70f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c70f-104">ID</span><span class="sxs-lookup"><span data-stu-id="1c70f-104">ID</span></span>|<span data-ttu-id="1c70f-105">1013</span><span class="sxs-lookup"><span data-stu-id="1c70f-105">1013</span></span>|  
|<span data-ttu-id="1c70f-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="1c70f-106">Keywords</span></span>|<span data-ttu-id="1c70f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1c70f-107">WFRuntime</span></span>|  
|<span data-ttu-id="1c70f-108">Nível</span><span class="sxs-lookup"><span data-stu-id="1c70f-108">Level</span></span>|<span data-ttu-id="1c70f-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="1c70f-109">Verbose</span></span>|  
|<span data-ttu-id="1c70f-110">Canal</span><span class="sxs-lookup"><span data-stu-id="1c70f-110">Channel</span></span>|<span data-ttu-id="1c70f-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="1c70f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1c70f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c70f-112">Description</span></span>  
 <span data-ttu-id="1c70f-113">Indica que um ExecuteActivityWorkItem concluiu</span><span class="sxs-lookup"><span data-stu-id="1c70f-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="1c70f-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="1c70f-114">Message</span></span>  
 <span data-ttu-id="1c70f-115">Um ExecuteActivityWorkItem concluiu para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="1c70f-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1c70f-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1c70f-116">Details</span></span>  
  
|<span data-ttu-id="1c70f-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="1c70f-117">Data Item Name</span></span>|<span data-ttu-id="1c70f-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="1c70f-118">Data Item Type</span></span>|<span data-ttu-id="1c70f-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c70f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1c70f-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="1c70f-120">Activity</span></span>|<span data-ttu-id="1c70f-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c70f-121">xs:string</span></span>|<span data-ttu-id="1c70f-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="1c70f-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="1c70f-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1c70f-123">DisplayName</span></span>|<span data-ttu-id="1c70f-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c70f-124">xs:string</span></span>|<span data-ttu-id="1c70f-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="1c70f-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="1c70f-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="1c70f-126">InstanceId</span></span>|<span data-ttu-id="1c70f-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c70f-127">xs:string</span></span>|<span data-ttu-id="1c70f-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="1c70f-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="1c70f-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1c70f-129">AppDomain</span></span>|<span data-ttu-id="1c70f-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c70f-130">xs:string</span></span>|<span data-ttu-id="1c70f-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1c70f-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
