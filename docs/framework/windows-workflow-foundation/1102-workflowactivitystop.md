---
title: 1102 - WorkflowActivityStop
ms.date: 03/30/2017
ms.assetid: 285e5cb8-e90d-4914-ac06-e9b176ffefa2
ms.openlocfilehash: 44617e9f53be0e601424746f83b171d33956197e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052788"
---
# <a name="1102---workflowactivitystop"></a><span data-ttu-id="9ef06-102">1102 - WorkflowActivityStop</span><span class="sxs-lookup"><span data-stu-id="9ef06-102">1102 - WorkflowActivityStop</span></span>
## <a name="properties"></a><span data-ttu-id="9ef06-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="9ef06-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ef06-104">ID</span><span class="sxs-lookup"><span data-stu-id="9ef06-104">ID</span></span>|<span data-ttu-id="9ef06-105">1102</span><span class="sxs-lookup"><span data-stu-id="9ef06-105">1102</span></span>|  
|<span data-ttu-id="9ef06-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="9ef06-106">Keywords</span></span>|<span data-ttu-id="9ef06-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9ef06-107">WFRuntime</span></span>|  
|<span data-ttu-id="9ef06-108">Nível</span><span class="sxs-lookup"><span data-stu-id="9ef06-108">Level</span></span>|<span data-ttu-id="9ef06-109">Informações</span><span class="sxs-lookup"><span data-stu-id="9ef06-109">Information</span></span>|  
|<span data-ttu-id="9ef06-110">Canal</span><span class="sxs-lookup"><span data-stu-id="9ef06-110">Channel</span></span>|<span data-ttu-id="9ef06-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="9ef06-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9ef06-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ef06-112">Description</span></span>  
 <span data-ttu-id="9ef06-113">Indica que uma atividade de fluxo de trabalho parou.</span><span class="sxs-lookup"><span data-stu-id="9ef06-113">Indicates a workflow activity has stopped.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9ef06-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="9ef06-114">Message</span></span>  
 <span data-ttu-id="9ef06-115">Identificação de WorkflowInstance: “%1" atividade de E2E</span><span class="sxs-lookup"><span data-stu-id="9ef06-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="9ef06-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="9ef06-116">Details</span></span>  
  
|<span data-ttu-id="9ef06-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="9ef06-117">Data Item Name</span></span>|<span data-ttu-id="9ef06-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="9ef06-118">Data Item Type</span></span>|<span data-ttu-id="9ef06-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ef06-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9ef06-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="9ef06-120">WorkflowInstanceId</span></span>|<span data-ttu-id="9ef06-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ef06-121">xs:string</span></span>|<span data-ttu-id="9ef06-122">A identificação de instância de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="9ef06-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="9ef06-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9ef06-123">AppDomain</span></span>|<span data-ttu-id="9ef06-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ef06-124">xs:string</span></span>|<span data-ttu-id="9ef06-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9ef06-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
