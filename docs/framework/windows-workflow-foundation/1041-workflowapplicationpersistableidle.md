---
title: 1041 - WorkflowApplicationPersistableIdle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ea6b31a83df6e15fe34f9e4be31a4eb53bc5bb51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="7795a-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="7795a-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="7795a-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7795a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7795a-104">ID</span><span class="sxs-lookup"><span data-stu-id="7795a-104">ID</span></span>|<span data-ttu-id="7795a-105">1041</span><span class="sxs-lookup"><span data-stu-id="7795a-105">1041</span></span>|  
|<span data-ttu-id="7795a-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="7795a-106">Keywords</span></span>|<span data-ttu-id="7795a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7795a-107">WFRuntime</span></span>|  
|<span data-ttu-id="7795a-108">Nível</span><span class="sxs-lookup"><span data-stu-id="7795a-108">Level</span></span>|<span data-ttu-id="7795a-109">Informações</span><span class="sxs-lookup"><span data-stu-id="7795a-109">Information</span></span>|  
|<span data-ttu-id="7795a-110">Canal</span><span class="sxs-lookup"><span data-stu-id="7795a-110">Channel</span></span>|<span data-ttu-id="7795a-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="7795a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7795a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7795a-112">Description</span></span>  
 <span data-ttu-id="7795a-113">Indica que um aplicativo de fluxo de trabalho estiver ocioso e persistable.</span><span class="sxs-lookup"><span data-stu-id="7795a-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="7795a-114">O aplicativo de fluxo de trabalho será rodado em marcha lento ou persistente.</span><span class="sxs-lookup"><span data-stu-id="7795a-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7795a-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="7795a-115">Message</span></span>  
 <span data-ttu-id="7795a-116">WorkflowApplication Id: '%1' está ociosa e persistente.</span><span class="sxs-lookup"><span data-stu-id="7795a-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="7795a-117">A seguinte ação será tomada: %2.</span><span class="sxs-lookup"><span data-stu-id="7795a-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7795a-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7795a-118">Details</span></span>  
  
|<span data-ttu-id="7795a-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="7795a-119">Data Item Name</span></span>|<span data-ttu-id="7795a-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="7795a-120">Data Item Type</span></span>|<span data-ttu-id="7795a-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="7795a-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7795a-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="7795a-122">WorkflowApplicationId</span></span>|<span data-ttu-id="7795a-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="7795a-123">xs:string</span></span>|<span data-ttu-id="7795a-124">A identificação do aplicativo de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7795a-124">The workflow application id</span></span>|  
|<span data-ttu-id="7795a-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="7795a-125">ActionTaken</span></span>|<span data-ttu-id="7795a-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="7795a-126">xs:string</span></span>|<span data-ttu-id="7795a-127">A ação a ser tomada no aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7795a-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="7795a-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7795a-128">AppDomain</span></span>|<span data-ttu-id="7795a-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="7795a-129">xs:string</span></span>|<span data-ttu-id="7795a-130">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7795a-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
