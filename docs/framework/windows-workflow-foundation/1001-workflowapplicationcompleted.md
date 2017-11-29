---
title: 1001 - WorkflowApplicationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a62a8448319e7b07a3ea302f00f2fa269bf654ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="0058b-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="0058b-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="0058b-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0058b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0058b-104">ID</span><span class="sxs-lookup"><span data-stu-id="0058b-104">ID</span></span>|<span data-ttu-id="0058b-105">1001</span><span class="sxs-lookup"><span data-stu-id="0058b-105">1001</span></span>|  
|<span data-ttu-id="0058b-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="0058b-106">Keywords</span></span>|<span data-ttu-id="0058b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0058b-107">WFRuntime</span></span>|  
|<span data-ttu-id="0058b-108">Nível</span><span class="sxs-lookup"><span data-stu-id="0058b-108">Level</span></span>|<span data-ttu-id="0058b-109">Informações</span><span class="sxs-lookup"><span data-stu-id="0058b-109">Information</span></span>|  
|<span data-ttu-id="0058b-110">Canal</span><span class="sxs-lookup"><span data-stu-id="0058b-110">Channel</span></span>|<span data-ttu-id="0058b-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="0058b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0058b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0058b-112">Description</span></span>  
 <span data-ttu-id="0058b-113">Indica que um aplicativo de fluxo de trabalho concluído no estado fechado.</span><span class="sxs-lookup"><span data-stu-id="0058b-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0058b-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="0058b-114">Message</span></span>  
 <span data-ttu-id="0058b-115">Identificação de WorkflowInstance: “%1 " terminou no estado fechado.</span><span class="sxs-lookup"><span data-stu-id="0058b-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0058b-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="0058b-116">Details</span></span>  
  
|<span data-ttu-id="0058b-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="0058b-117">Data Item Name</span></span>|<span data-ttu-id="0058b-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="0058b-118">Data Item Type</span></span>|<span data-ttu-id="0058b-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0058b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0058b-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="0058b-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="0058b-121">A identificação de instância para o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0058b-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="0058b-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0058b-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0058b-123">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0058b-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
