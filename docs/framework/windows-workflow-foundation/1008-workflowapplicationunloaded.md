---
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: c7c22e6e4270a3fc3e91e1711db5da9bd5a378b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925223"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="e0b13-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="e0b13-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="e0b13-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e0b13-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e0b13-104">ID</span><span class="sxs-lookup"><span data-stu-id="e0b13-104">ID</span></span>|<span data-ttu-id="e0b13-105">1008</span><span class="sxs-lookup"><span data-stu-id="e0b13-105">1008</span></span>|  
|<span data-ttu-id="e0b13-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="e0b13-106">Keywords</span></span>|<span data-ttu-id="e0b13-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e0b13-107">WFRuntime</span></span>|  
|<span data-ttu-id="e0b13-108">Nível</span><span class="sxs-lookup"><span data-stu-id="e0b13-108">Level</span></span>|<span data-ttu-id="e0b13-109">Informações</span><span class="sxs-lookup"><span data-stu-id="e0b13-109">Information</span></span>|  
|<span data-ttu-id="e0b13-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e0b13-110">Channel</span></span>|<span data-ttu-id="e0b13-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="e0b13-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e0b13-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0b13-112">Description</span></span>  
 <span data-ttu-id="e0b13-113">Indica que um aplicativo de fluxo de trabalho descarregou.</span><span class="sxs-lookup"><span data-stu-id="e0b13-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e0b13-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="e0b13-114">Message</span></span>  
 <span data-ttu-id="e0b13-115">Identificação de WorkflowInstance: “%1" foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="e0b13-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e0b13-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e0b13-116">Details</span></span>  
  
|<span data-ttu-id="e0b13-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="e0b13-117">Data Item Name</span></span>|<span data-ttu-id="e0b13-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="e0b13-118">Data Item Type</span></span>|<span data-ttu-id="e0b13-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0b13-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e0b13-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="e0b13-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="e0b13-121">A identificação de instância para o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="e0b13-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="e0b13-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e0b13-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e0b13-123">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e0b13-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
