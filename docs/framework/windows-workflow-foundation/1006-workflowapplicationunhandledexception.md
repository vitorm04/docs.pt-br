---
title: 1006 - WorkflowApplicationUnhandledException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 842d6bb6172eed5f7382633119045ea7507fb955
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="0b6f0-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="0b6f0-102">1006 - WorkflowApplicationUnhandledException</span></span>
## <a name="properties"></a><span data-ttu-id="0b6f0-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0b6f0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0b6f0-104">ID</span><span class="sxs-lookup"><span data-stu-id="0b6f0-104">ID</span></span>|<span data-ttu-id="0b6f0-105">1006</span><span class="sxs-lookup"><span data-stu-id="0b6f0-105">1006</span></span>|  
|<span data-ttu-id="0b6f0-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="0b6f0-106">Keywords</span></span>|<span data-ttu-id="0b6f0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0b6f0-107">WFRuntime</span></span>|  
|<span data-ttu-id="0b6f0-108">Nível</span><span class="sxs-lookup"><span data-stu-id="0b6f0-108">Level</span></span>|<span data-ttu-id="0b6f0-109">Erro</span><span class="sxs-lookup"><span data-stu-id="0b6f0-109">Error</span></span>|  
|<span data-ttu-id="0b6f0-110">Canal</span><span class="sxs-lookup"><span data-stu-id="0b6f0-110">Channel</span></span>|<span data-ttu-id="0b6f0-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="0b6f0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0b6f0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b6f0-112">Description</span></span>  
 <span data-ttu-id="0b6f0-113">Indica que um aplicativo de fluxo de trabalho após uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="0b6f0-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0b6f0-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="0b6f0-114">Message</span></span>  
 <span data-ttu-id="0b6f0-115">WorkflowInstance Id: '%1' encontrou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="0b6f0-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="0b6f0-116">A exceção se originou da atividade '%2', DisplayName: '%3'.</span><span class="sxs-lookup"><span data-stu-id="0b6f0-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="0b6f0-117">A seguinte ação será tomada: %4.</span><span class="sxs-lookup"><span data-stu-id="0b6f0-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0b6f0-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="0b6f0-118">Details</span></span>  
  
|<span data-ttu-id="0b6f0-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="0b6f0-119">Data Item Name</span></span>|<span data-ttu-id="0b6f0-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="0b6f0-120">Data Item Type</span></span>|<span data-ttu-id="0b6f0-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b6f0-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0b6f0-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="0b6f0-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="0b6f0-123">A identificação de instância para o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0b6f0-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="0b6f0-124">Exceção</span><span class="sxs-lookup"><span data-stu-id="0b6f0-124">Exception</span></span>|`xs:string`|<span data-ttu-id="0b6f0-125">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="0b6f0-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="0b6f0-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0b6f0-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0b6f0-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0b6f0-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
