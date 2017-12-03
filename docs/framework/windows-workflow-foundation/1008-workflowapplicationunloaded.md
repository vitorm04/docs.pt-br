---
title: 1008 - WorkflowApplicationUnloaded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dedb1dd389e2308ea8f70d71f057d17a45172517
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="f3976-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="f3976-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="f3976-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f3976-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f3976-104">ID</span><span class="sxs-lookup"><span data-stu-id="f3976-104">ID</span></span>|<span data-ttu-id="f3976-105">1008</span><span class="sxs-lookup"><span data-stu-id="f3976-105">1008</span></span>|  
|<span data-ttu-id="f3976-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="f3976-106">Keywords</span></span>|<span data-ttu-id="f3976-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f3976-107">WFRuntime</span></span>|  
|<span data-ttu-id="f3976-108">Nível</span><span class="sxs-lookup"><span data-stu-id="f3976-108">Level</span></span>|<span data-ttu-id="f3976-109">Informações</span><span class="sxs-lookup"><span data-stu-id="f3976-109">Information</span></span>|  
|<span data-ttu-id="f3976-110">Canal</span><span class="sxs-lookup"><span data-stu-id="f3976-110">Channel</span></span>|<span data-ttu-id="f3976-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="f3976-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f3976-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3976-112">Description</span></span>  
 <span data-ttu-id="f3976-113">Indica que um aplicativo de fluxo de trabalho descarregou.</span><span class="sxs-lookup"><span data-stu-id="f3976-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f3976-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="f3976-114">Message</span></span>  
 <span data-ttu-id="f3976-115">Identificação de WorkflowInstance: “%1" foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="f3976-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f3976-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f3976-116">Details</span></span>  
  
|<span data-ttu-id="f3976-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="f3976-117">Data Item Name</span></span>|<span data-ttu-id="f3976-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="f3976-118">Data Item Type</span></span>|<span data-ttu-id="f3976-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3976-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f3976-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="f3976-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="f3976-121">A identificação de instância para o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f3976-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="f3976-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f3976-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f3976-123">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f3976-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
