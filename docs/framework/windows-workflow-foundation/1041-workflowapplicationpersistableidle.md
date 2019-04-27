---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 07be0ae603443a1ef06cb539bba7b227d7b3e325
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924183"
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="a459c-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="a459c-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="a459c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a459c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a459c-104">ID</span><span class="sxs-lookup"><span data-stu-id="a459c-104">ID</span></span>|<span data-ttu-id="a459c-105">1041</span><span class="sxs-lookup"><span data-stu-id="a459c-105">1041</span></span>|  
|<span data-ttu-id="a459c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="a459c-106">Keywords</span></span>|<span data-ttu-id="a459c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a459c-107">WFRuntime</span></span>|  
|<span data-ttu-id="a459c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="a459c-108">Level</span></span>|<span data-ttu-id="a459c-109">Informações</span><span class="sxs-lookup"><span data-stu-id="a459c-109">Information</span></span>|  
|<span data-ttu-id="a459c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="a459c-110">Channel</span></span>|<span data-ttu-id="a459c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="a459c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a459c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a459c-112">Description</span></span>  
 <span data-ttu-id="a459c-113">Indica que um aplicativo de fluxo de trabalho estiver ocioso e persistable.</span><span class="sxs-lookup"><span data-stu-id="a459c-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="a459c-114">O aplicativo de fluxo de trabalho será rodado em marcha lento ou persistente.</span><span class="sxs-lookup"><span data-stu-id="a459c-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a459c-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="a459c-115">Message</span></span>  
 <span data-ttu-id="a459c-116">Identificação de WorkflowApplication: "%1" estiver ocioso e persistable.</span><span class="sxs-lookup"><span data-stu-id="a459c-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="a459c-117">A seguir ação será necessária: %2.</span><span class="sxs-lookup"><span data-stu-id="a459c-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a459c-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a459c-118">Details</span></span>  
  
|<span data-ttu-id="a459c-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="a459c-119">Data Item Name</span></span>|<span data-ttu-id="a459c-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="a459c-120">Data Item Type</span></span>|<span data-ttu-id="a459c-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="a459c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a459c-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="a459c-122">WorkflowApplicationId</span></span>|<span data-ttu-id="a459c-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="a459c-123">xs:string</span></span>|<span data-ttu-id="a459c-124">A identificação do aplicativo de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a459c-124">The workflow application id</span></span>|  
|<span data-ttu-id="a459c-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="a459c-125">ActionTaken</span></span>|<span data-ttu-id="a459c-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="a459c-126">xs:string</span></span>|<span data-ttu-id="a459c-127">A ação a ser tomada no aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a459c-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="a459c-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a459c-128">AppDomain</span></span>|<span data-ttu-id="a459c-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="a459c-129">xs:string</span></span>|<span data-ttu-id="a459c-130">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a459c-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
