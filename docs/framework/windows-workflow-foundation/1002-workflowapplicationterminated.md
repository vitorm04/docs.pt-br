---
title: 1002 - WorkflowApplicationTerminated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 93a6a400576df84faae3cd58940462255b0073c6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="b3b9c-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="b3b9c-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="b3b9c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b3b9c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b3b9c-104">ID</span><span class="sxs-lookup"><span data-stu-id="b3b9c-104">ID</span></span>|<span data-ttu-id="b3b9c-105">1002</span><span class="sxs-lookup"><span data-stu-id="b3b9c-105">1002</span></span>|  
|<span data-ttu-id="b3b9c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="b3b9c-106">Keywords</span></span>|<span data-ttu-id="b3b9c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b3b9c-107">WFRuntime</span></span>|  
|<span data-ttu-id="b3b9c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="b3b9c-108">Level</span></span>|<span data-ttu-id="b3b9c-109">Informações</span><span class="sxs-lookup"><span data-stu-id="b3b9c-109">Information</span></span>|  
|<span data-ttu-id="b3b9c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="b3b9c-110">Channel</span></span>|<span data-ttu-id="b3b9c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="b3b9c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b3b9c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3b9c-112">Description</span></span>  
 <span data-ttu-id="b3b9c-113">Indica que um aplicativo de fluxo de trabalho foi finalizado no estado criticado com uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b3b9c-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b3b9c-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="b3b9c-114">Message</span></span>  
 <span data-ttu-id="b3b9c-115">Identificação de WorkflowApplication: “%1 " foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="b3b9c-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="b3b9c-116">Foi concluído em estado Faulted (com falha) com uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b3b9c-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b3b9c-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="b3b9c-117">Details</span></span>  
  
|<span data-ttu-id="b3b9c-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="b3b9c-118">Data Item Name</span></span>|<span data-ttu-id="b3b9c-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="b3b9c-119">Data Item Type</span></span>|<span data-ttu-id="b3b9c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3b9c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b3b9c-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="b3b9c-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="b3b9c-122">A identificação do aplicativo de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b3b9c-122">The workflow application id</span></span>|  
|<span data-ttu-id="b3b9c-123">Exceção</span><span class="sxs-lookup"><span data-stu-id="b3b9c-123">Exception</span></span>|`xs:string`|<span data-ttu-id="b3b9c-124">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="b3b9c-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="b3b9c-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b3b9c-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b3b9c-126">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b3b9c-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
