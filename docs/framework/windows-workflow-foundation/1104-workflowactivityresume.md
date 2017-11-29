---
title: 1104 - WorkflowActivityResume
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fe95d1e-34bd-43ca-b92e-587d2d248fff
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8ffba47fa7cd865b604704a3819cbe89be1ed5cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1104---workflowactivityresume"></a><span data-ttu-id="96274-102">1104 - WorkflowActivityResume</span><span class="sxs-lookup"><span data-stu-id="96274-102">1104 - WorkflowActivityResume</span></span>
## <a name="properties"></a><span data-ttu-id="96274-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="96274-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="96274-104">ID</span><span class="sxs-lookup"><span data-stu-id="96274-104">ID</span></span>|<span data-ttu-id="96274-105">1104</span><span class="sxs-lookup"><span data-stu-id="96274-105">1104</span></span>|  
|<span data-ttu-id="96274-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="96274-106">Keywords</span></span>|<span data-ttu-id="96274-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="96274-107">WFRuntime</span></span>|  
|<span data-ttu-id="96274-108">Nível</span><span class="sxs-lookup"><span data-stu-id="96274-108">Level</span></span>|<span data-ttu-id="96274-109">Informações</span><span class="sxs-lookup"><span data-stu-id="96274-109">Information</span></span>|  
|<span data-ttu-id="96274-110">Canal</span><span class="sxs-lookup"><span data-stu-id="96274-110">Channel</span></span>|<span data-ttu-id="96274-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="96274-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="96274-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="96274-112">Description</span></span>  
 <span data-ttu-id="96274-113">Indica que uma atividade do fluxo de trabalho foi continuada.</span><span class="sxs-lookup"><span data-stu-id="96274-113">Indicates a workflow activity has been resumed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="96274-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="96274-114">Message</span></span>  
 <span data-ttu-id="96274-115">Identificação de WorkflowInstance: “%1" atividade de E2E</span><span class="sxs-lookup"><span data-stu-id="96274-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="96274-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="96274-116">Details</span></span>  
  
|<span data-ttu-id="96274-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="96274-117">Data Item Name</span></span>|<span data-ttu-id="96274-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="96274-118">Data Item Type</span></span>|<span data-ttu-id="96274-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="96274-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="96274-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="96274-120">WorkflowInstanceId</span></span>|<span data-ttu-id="96274-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="96274-121">xs:string</span></span>|<span data-ttu-id="96274-122">A identificação de instância de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="96274-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="96274-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="96274-123">AppDomain</span></span>|<span data-ttu-id="96274-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="96274-124">xs:string</span></span>|<span data-ttu-id="96274-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="96274-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
