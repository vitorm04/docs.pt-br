---
title: 1101 - WorkflowActivityStart
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 831cd386-b9b5-47a9-9690-aff6292ff348
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d89b6f41838ee89b503746be4020b93db0ac96e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1101---workflowactivitystart"></a><span data-ttu-id="376cf-102">1101 - WorkflowActivityStart</span><span class="sxs-lookup"><span data-stu-id="376cf-102">1101 - WorkflowActivityStart</span></span>
## <a name="properties"></a><span data-ttu-id="376cf-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="376cf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="376cf-104">ID</span><span class="sxs-lookup"><span data-stu-id="376cf-104">ID</span></span>|<span data-ttu-id="376cf-105">1101</span><span class="sxs-lookup"><span data-stu-id="376cf-105">1101</span></span>|  
|<span data-ttu-id="376cf-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="376cf-106">Keywords</span></span>|<span data-ttu-id="376cf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="376cf-107">WFRuntime</span></span>|  
|<span data-ttu-id="376cf-108">Nível</span><span class="sxs-lookup"><span data-stu-id="376cf-108">Level</span></span>|<span data-ttu-id="376cf-109">Informações</span><span class="sxs-lookup"><span data-stu-id="376cf-109">Information</span></span>|  
|<span data-ttu-id="376cf-110">Canal</span><span class="sxs-lookup"><span data-stu-id="376cf-110">Channel</span></span>|<span data-ttu-id="376cf-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="376cf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="376cf-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="376cf-112">Description</span></span>  
 <span data-ttu-id="376cf-113">Indica que uma atividade de fluxo de trabalho foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="376cf-113">Indicates a workflow activity has started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="376cf-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="376cf-114">Message</span></span>  
 <span data-ttu-id="376cf-115">Identificação de WorkflowInstance: “%1" atividade de E2E</span><span class="sxs-lookup"><span data-stu-id="376cf-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="376cf-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="376cf-116">Details</span></span>  
  
|<span data-ttu-id="376cf-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="376cf-117">Data Item Name</span></span>|<span data-ttu-id="376cf-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="376cf-118">Data Item Type</span></span>|<span data-ttu-id="376cf-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="376cf-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="376cf-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="376cf-120">WorkflowInstanceId</span></span>|<span data-ttu-id="376cf-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="376cf-121">xs:string</span></span>|<span data-ttu-id="376cf-122">A identificação de instância de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="376cf-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="376cf-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="376cf-123">AppDomain</span></span>|<span data-ttu-id="376cf-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="376cf-124">xs:string</span></span>|<span data-ttu-id="376cf-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="376cf-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
