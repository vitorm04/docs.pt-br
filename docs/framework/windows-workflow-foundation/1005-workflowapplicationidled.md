---
title: 1005 - WorkflowApplicationIdled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 42d22a7187adc712c0f236111cecac89dd59e2f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="934ad-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="934ad-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="934ad-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="934ad-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="934ad-104">ID</span><span class="sxs-lookup"><span data-stu-id="934ad-104">ID</span></span>|<span data-ttu-id="934ad-105">1005</span><span class="sxs-lookup"><span data-stu-id="934ad-105">1005</span></span>|  
|<span data-ttu-id="934ad-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="934ad-106">Keywords</span></span>|<span data-ttu-id="934ad-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="934ad-107">WFRuntime</span></span>|  
|<span data-ttu-id="934ad-108">Nível</span><span class="sxs-lookup"><span data-stu-id="934ad-108">Level</span></span>|<span data-ttu-id="934ad-109">Informações</span><span class="sxs-lookup"><span data-stu-id="934ad-109">Information</span></span>|  
|<span data-ttu-id="934ad-110">Canal</span><span class="sxs-lookup"><span data-stu-id="934ad-110">Channel</span></span>|<span data-ttu-id="934ad-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="934ad-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="934ad-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="934ad-112">Description</span></span>  
 <span data-ttu-id="934ad-113">Indica que um aplicativo de fluxo de trabalho rodou em marcha lenta.</span><span class="sxs-lookup"><span data-stu-id="934ad-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="934ad-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="934ad-114">Message</span></span>  
 <span data-ttu-id="934ad-115">Identificação de WorkflowApplication: “%1 " foi ociosa.</span><span class="sxs-lookup"><span data-stu-id="934ad-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="934ad-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="934ad-116">Details</span></span>  
  
|<span data-ttu-id="934ad-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="934ad-117">Data Item Name</span></span>|<span data-ttu-id="934ad-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="934ad-118">Data Item Type</span></span>|<span data-ttu-id="934ad-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="934ad-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="934ad-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="934ad-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="934ad-121">A identificação do aplicativo de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="934ad-121">The workflow application id</span></span>|  
|<span data-ttu-id="934ad-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="934ad-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="934ad-123">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="934ad-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
