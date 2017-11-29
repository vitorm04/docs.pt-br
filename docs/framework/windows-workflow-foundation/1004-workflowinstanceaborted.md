---
title: 1004 - WorkflowInstanceAborted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7394ebbcb14850af89d906b0b573c4f677346825
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="9bc21-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="9bc21-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="9bc21-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="9bc21-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9bc21-104">ID</span><span class="sxs-lookup"><span data-stu-id="9bc21-104">ID</span></span>|<span data-ttu-id="9bc21-105">1004</span><span class="sxs-lookup"><span data-stu-id="9bc21-105">1004</span></span>|  
|<span data-ttu-id="9bc21-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="9bc21-106">Keywords</span></span>|<span data-ttu-id="9bc21-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9bc21-107">WFRuntime</span></span>|  
|<span data-ttu-id="9bc21-108">Nível</span><span class="sxs-lookup"><span data-stu-id="9bc21-108">Level</span></span>|<span data-ttu-id="9bc21-109">Informações</span><span class="sxs-lookup"><span data-stu-id="9bc21-109">Information</span></span>|  
|<span data-ttu-id="9bc21-110">Canal</span><span class="sxs-lookup"><span data-stu-id="9bc21-110">Channel</span></span>|<span data-ttu-id="9bc21-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="9bc21-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9bc21-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bc21-112">Description</span></span>  
 <span data-ttu-id="9bc21-113">Indica que uma instância de worfklow anulou com uma exceção.</span><span class="sxs-lookup"><span data-stu-id="9bc21-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9bc21-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="9bc21-114">Message</span></span>  
 <span data-ttu-id="9bc21-115">Identificação de WorkflowInstance: “%1 " foi anuladas com uma exceção.</span><span class="sxs-lookup"><span data-stu-id="9bc21-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9bc21-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="9bc21-116">Details</span></span>  
  
|<span data-ttu-id="9bc21-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="9bc21-117">Data Item Name</span></span>|<span data-ttu-id="9bc21-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="9bc21-118">Data Item Type</span></span>|<span data-ttu-id="9bc21-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bc21-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9bc21-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="9bc21-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="9bc21-121">A identificação de instância para o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="9bc21-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="9bc21-122">Exceção</span><span class="sxs-lookup"><span data-stu-id="9bc21-122">Exception</span></span>|`xs:string`|<span data-ttu-id="9bc21-123">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="9bc21-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="9bc21-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9bc21-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9bc21-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9bc21-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
