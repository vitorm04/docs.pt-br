---
title: 1003 - WorkflowInstanceCanceled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b264450703090edfcf99f9584c16d33eb82a76e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="e39c1-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="e39c1-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="e39c1-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e39c1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e39c1-104">ID</span><span class="sxs-lookup"><span data-stu-id="e39c1-104">ID</span></span>|<span data-ttu-id="e39c1-105">1003</span><span class="sxs-lookup"><span data-stu-id="e39c1-105">1003</span></span>|  
|<span data-ttu-id="e39c1-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="e39c1-106">Keywords</span></span>|<span data-ttu-id="e39c1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e39c1-107">WFRuntime</span></span>|  
|<span data-ttu-id="e39c1-108">Nível</span><span class="sxs-lookup"><span data-stu-id="e39c1-108">Level</span></span>|<span data-ttu-id="e39c1-109">Informações</span><span class="sxs-lookup"><span data-stu-id="e39c1-109">Information</span></span>|  
|<span data-ttu-id="e39c1-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e39c1-110">Channel</span></span>|<span data-ttu-id="e39c1-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="e39c1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e39c1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e39c1-112">Description</span></span>  
 <span data-ttu-id="e39c1-113">Indica que uma instância de fluxo de trabalho concluído no estado cancelado.</span><span class="sxs-lookup"><span data-stu-id="e39c1-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e39c1-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="e39c1-114">Message</span></span>  
 <span data-ttu-id="e39c1-115">Identificação de WorkflowInstance: “%1 " terminou no estado cancelado.</span><span class="sxs-lookup"><span data-stu-id="e39c1-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e39c1-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e39c1-116">Details</span></span>  
  
|<span data-ttu-id="e39c1-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="e39c1-117">Data Item Name</span></span>|<span data-ttu-id="e39c1-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="e39c1-118">Data Item Type</span></span>|<span data-ttu-id="e39c1-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="e39c1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e39c1-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="e39c1-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="e39c1-121">A identificação de instância para o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e39c1-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="e39c1-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e39c1-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e39c1-123">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e39c1-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
