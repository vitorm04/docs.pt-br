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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b287c99453724f855a51e9a1b8068337dd5e373
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="235d8-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="235d8-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="235d8-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="235d8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="235d8-104">ID</span><span class="sxs-lookup"><span data-stu-id="235d8-104">ID</span></span>|<span data-ttu-id="235d8-105">1003</span><span class="sxs-lookup"><span data-stu-id="235d8-105">1003</span></span>|  
|<span data-ttu-id="235d8-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="235d8-106">Keywords</span></span>|<span data-ttu-id="235d8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="235d8-107">WFRuntime</span></span>|  
|<span data-ttu-id="235d8-108">Nível</span><span class="sxs-lookup"><span data-stu-id="235d8-108">Level</span></span>|<span data-ttu-id="235d8-109">Informações</span><span class="sxs-lookup"><span data-stu-id="235d8-109">Information</span></span>|  
|<span data-ttu-id="235d8-110">Canal</span><span class="sxs-lookup"><span data-stu-id="235d8-110">Channel</span></span>|<span data-ttu-id="235d8-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="235d8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="235d8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="235d8-112">Description</span></span>  
 <span data-ttu-id="235d8-113">Indica que uma instância de fluxo de trabalho concluído no estado cancelado.</span><span class="sxs-lookup"><span data-stu-id="235d8-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="235d8-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="235d8-114">Message</span></span>  
 <span data-ttu-id="235d8-115">Identificação de WorkflowInstance: “%1 " terminou no estado cancelado.</span><span class="sxs-lookup"><span data-stu-id="235d8-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="235d8-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="235d8-116">Details</span></span>  
  
|<span data-ttu-id="235d8-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="235d8-117">Data Item Name</span></span>|<span data-ttu-id="235d8-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="235d8-118">Data Item Type</span></span>|<span data-ttu-id="235d8-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="235d8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="235d8-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="235d8-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="235d8-121">A identificação de instância para o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="235d8-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="235d8-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="235d8-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="235d8-123">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="235d8-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
