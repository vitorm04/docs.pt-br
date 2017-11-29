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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 297b3ad9a677d28d12d1b00fdaeec8ec94842263
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="743c0-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="743c0-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="743c0-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="743c0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="743c0-104">ID</span><span class="sxs-lookup"><span data-stu-id="743c0-104">ID</span></span>|<span data-ttu-id="743c0-105">1008</span><span class="sxs-lookup"><span data-stu-id="743c0-105">1008</span></span>|  
|<span data-ttu-id="743c0-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="743c0-106">Keywords</span></span>|<span data-ttu-id="743c0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="743c0-107">WFRuntime</span></span>|  
|<span data-ttu-id="743c0-108">Nível</span><span class="sxs-lookup"><span data-stu-id="743c0-108">Level</span></span>|<span data-ttu-id="743c0-109">Informações</span><span class="sxs-lookup"><span data-stu-id="743c0-109">Information</span></span>|  
|<span data-ttu-id="743c0-110">Canal</span><span class="sxs-lookup"><span data-stu-id="743c0-110">Channel</span></span>|<span data-ttu-id="743c0-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="743c0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="743c0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="743c0-112">Description</span></span>  
 <span data-ttu-id="743c0-113">Indica que um aplicativo de fluxo de trabalho descarregou.</span><span class="sxs-lookup"><span data-stu-id="743c0-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="743c0-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="743c0-114">Message</span></span>  
 <span data-ttu-id="743c0-115">Identificação de WorkflowInstance: “%1" foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="743c0-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="743c0-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="743c0-116">Details</span></span>  
  
|<span data-ttu-id="743c0-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="743c0-117">Data Item Name</span></span>|<span data-ttu-id="743c0-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="743c0-118">Data Item Type</span></span>|<span data-ttu-id="743c0-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="743c0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="743c0-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="743c0-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="743c0-121">A identificação de instância para o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="743c0-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="743c0-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="743c0-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="743c0-123">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="743c0-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
