---
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: c76a2dab6a95bda7f3969af07f814aba30071c7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008623"
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="77780-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="77780-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="77780-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="77780-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77780-104">ID</span><span class="sxs-lookup"><span data-stu-id="77780-104">ID</span></span>|<span data-ttu-id="77780-105">1003</span><span class="sxs-lookup"><span data-stu-id="77780-105">1003</span></span>|  
|<span data-ttu-id="77780-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="77780-106">Keywords</span></span>|<span data-ttu-id="77780-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="77780-107">WFRuntime</span></span>|  
|<span data-ttu-id="77780-108">Nível</span><span class="sxs-lookup"><span data-stu-id="77780-108">Level</span></span>|<span data-ttu-id="77780-109">Informações</span><span class="sxs-lookup"><span data-stu-id="77780-109">Information</span></span>|  
|<span data-ttu-id="77780-110">Canal</span><span class="sxs-lookup"><span data-stu-id="77780-110">Channel</span></span>|<span data-ttu-id="77780-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="77780-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="77780-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="77780-112">Description</span></span>  
 <span data-ttu-id="77780-113">Indica que uma instância de fluxo de trabalho concluído no estado cancelado.</span><span class="sxs-lookup"><span data-stu-id="77780-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="77780-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="77780-114">Message</span></span>  
 <span data-ttu-id="77780-115">Identificação de WorkflowInstance: “%1 " terminou no estado cancelado.</span><span class="sxs-lookup"><span data-stu-id="77780-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="77780-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="77780-116">Details</span></span>  
  
|<span data-ttu-id="77780-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="77780-117">Data Item Name</span></span>|<span data-ttu-id="77780-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="77780-118">Data Item Type</span></span>|<span data-ttu-id="77780-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="77780-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="77780-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="77780-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="77780-121">A identificação de instância para o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="77780-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="77780-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="77780-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="77780-123">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="77780-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
