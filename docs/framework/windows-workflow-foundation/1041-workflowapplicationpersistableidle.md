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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1efc32ed0304d5b0d222054e5c65abe279ef93ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="b6490-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="b6490-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="b6490-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b6490-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b6490-104">ID</span><span class="sxs-lookup"><span data-stu-id="b6490-104">ID</span></span>|<span data-ttu-id="b6490-105">1041</span><span class="sxs-lookup"><span data-stu-id="b6490-105">1041</span></span>|  
|<span data-ttu-id="b6490-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="b6490-106">Keywords</span></span>|<span data-ttu-id="b6490-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b6490-107">WFRuntime</span></span>|  
|<span data-ttu-id="b6490-108">Nível</span><span class="sxs-lookup"><span data-stu-id="b6490-108">Level</span></span>|<span data-ttu-id="b6490-109">Informações</span><span class="sxs-lookup"><span data-stu-id="b6490-109">Information</span></span>|  
|<span data-ttu-id="b6490-110">Canal</span><span class="sxs-lookup"><span data-stu-id="b6490-110">Channel</span></span>|<span data-ttu-id="b6490-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="b6490-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b6490-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6490-112">Description</span></span>  
 <span data-ttu-id="b6490-113">Indica que um aplicativo de fluxo de trabalho estiver ocioso e persistable.</span><span class="sxs-lookup"><span data-stu-id="b6490-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="b6490-114">O aplicativo de fluxo de trabalho será rodado em marcha lento ou persistente.</span><span class="sxs-lookup"><span data-stu-id="b6490-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b6490-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="b6490-115">Message</span></span>  
 <span data-ttu-id="b6490-116">WorkflowApplication Id: '%1' está ociosa e persistente.</span><span class="sxs-lookup"><span data-stu-id="b6490-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="b6490-117">A seguinte ação será tomada: %2.</span><span class="sxs-lookup"><span data-stu-id="b6490-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b6490-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="b6490-118">Details</span></span>  
  
|<span data-ttu-id="b6490-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="b6490-119">Data Item Name</span></span>|<span data-ttu-id="b6490-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="b6490-120">Data Item Type</span></span>|<span data-ttu-id="b6490-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6490-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b6490-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="b6490-122">WorkflowApplicationId</span></span>|<span data-ttu-id="b6490-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="b6490-123">xs:string</span></span>|<span data-ttu-id="b6490-124">A identificação do aplicativo de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b6490-124">The workflow application id</span></span>|  
|<span data-ttu-id="b6490-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="b6490-125">ActionTaken</span></span>|<span data-ttu-id="b6490-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="b6490-126">xs:string</span></span>|<span data-ttu-id="b6490-127">A ação a ser tomada no aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6490-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="b6490-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b6490-128">AppDomain</span></span>|<span data-ttu-id="b6490-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="b6490-129">xs:string</span></span>|<span data-ttu-id="b6490-130">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b6490-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
