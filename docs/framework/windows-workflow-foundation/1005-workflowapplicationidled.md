---
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 6bbd12e8025b6a127dbfec8e5d3690825c188c4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509288"
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="ef88a-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="ef88a-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="ef88a-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ef88a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ef88a-104">ID</span><span class="sxs-lookup"><span data-stu-id="ef88a-104">ID</span></span>|<span data-ttu-id="ef88a-105">1005</span><span class="sxs-lookup"><span data-stu-id="ef88a-105">1005</span></span>|  
|<span data-ttu-id="ef88a-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="ef88a-106">Keywords</span></span>|<span data-ttu-id="ef88a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ef88a-107">WFRuntime</span></span>|  
|<span data-ttu-id="ef88a-108">Nível</span><span class="sxs-lookup"><span data-stu-id="ef88a-108">Level</span></span>|<span data-ttu-id="ef88a-109">Informações</span><span class="sxs-lookup"><span data-stu-id="ef88a-109">Information</span></span>|  
|<span data-ttu-id="ef88a-110">Canal</span><span class="sxs-lookup"><span data-stu-id="ef88a-110">Channel</span></span>|<span data-ttu-id="ef88a-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="ef88a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ef88a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef88a-112">Description</span></span>  
 <span data-ttu-id="ef88a-113">Indica que um aplicativo de fluxo de trabalho rodou em marcha lenta.</span><span class="sxs-lookup"><span data-stu-id="ef88a-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ef88a-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="ef88a-114">Message</span></span>  
 <span data-ttu-id="ef88a-115">Identificação de WorkflowApplication: “%1 " foi ociosa.</span><span class="sxs-lookup"><span data-stu-id="ef88a-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ef88a-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ef88a-116">Details</span></span>  
  
|<span data-ttu-id="ef88a-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="ef88a-117">Data Item Name</span></span>|<span data-ttu-id="ef88a-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="ef88a-118">Data Item Type</span></span>|<span data-ttu-id="ef88a-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef88a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ef88a-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="ef88a-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="ef88a-121">A identificação do aplicativo de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="ef88a-121">The workflow application id</span></span>|  
|<span data-ttu-id="ef88a-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ef88a-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ef88a-123">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ef88a-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
