---
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d1eaf3cf107a6b5e244cc2d9372ee68d387ef6c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510660"
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="4ddb8-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="4ddb8-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="4ddb8-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4ddb8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4ddb8-104">ID</span><span class="sxs-lookup"><span data-stu-id="4ddb8-104">ID</span></span>|<span data-ttu-id="4ddb8-105">1004</span><span class="sxs-lookup"><span data-stu-id="4ddb8-105">1004</span></span>|  
|<span data-ttu-id="4ddb8-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="4ddb8-106">Keywords</span></span>|<span data-ttu-id="4ddb8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4ddb8-107">WFRuntime</span></span>|  
|<span data-ttu-id="4ddb8-108">Nível</span><span class="sxs-lookup"><span data-stu-id="4ddb8-108">Level</span></span>|<span data-ttu-id="4ddb8-109">Informações</span><span class="sxs-lookup"><span data-stu-id="4ddb8-109">Information</span></span>|  
|<span data-ttu-id="4ddb8-110">Canal</span><span class="sxs-lookup"><span data-stu-id="4ddb8-110">Channel</span></span>|<span data-ttu-id="4ddb8-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="4ddb8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4ddb8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4ddb8-112">Description</span></span>  
 <span data-ttu-id="4ddb8-113">Indica que uma instância de worfklow anulou com uma exceção.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4ddb8-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="4ddb8-114">Message</span></span>  
 <span data-ttu-id="4ddb8-115">Identificação de WorkflowInstance: “%1 " foi anuladas com uma exceção.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4ddb8-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4ddb8-116">Details</span></span>  
  
|<span data-ttu-id="4ddb8-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="4ddb8-117">Data Item Name</span></span>|<span data-ttu-id="4ddb8-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="4ddb8-118">Data Item Type</span></span>|<span data-ttu-id="4ddb8-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="4ddb8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4ddb8-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="4ddb8-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="4ddb8-121">A identificação de instância para o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4ddb8-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="4ddb8-122">Exceção</span><span class="sxs-lookup"><span data-stu-id="4ddb8-122">Exception</span></span>|`xs:string`|<span data-ttu-id="4ddb8-123">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="4ddb8-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="4ddb8-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4ddb8-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4ddb8-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
