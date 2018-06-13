---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 07be0ae603443a1ef06cb539bba7b227d7b3e325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509632"
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="83b90-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="83b90-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="83b90-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="83b90-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="83b90-104">ID</span><span class="sxs-lookup"><span data-stu-id="83b90-104">ID</span></span>|<span data-ttu-id="83b90-105">1041</span><span class="sxs-lookup"><span data-stu-id="83b90-105">1041</span></span>|  
|<span data-ttu-id="83b90-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="83b90-106">Keywords</span></span>|<span data-ttu-id="83b90-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="83b90-107">WFRuntime</span></span>|  
|<span data-ttu-id="83b90-108">Nível</span><span class="sxs-lookup"><span data-stu-id="83b90-108">Level</span></span>|<span data-ttu-id="83b90-109">Informações</span><span class="sxs-lookup"><span data-stu-id="83b90-109">Information</span></span>|  
|<span data-ttu-id="83b90-110">Canal</span><span class="sxs-lookup"><span data-stu-id="83b90-110">Channel</span></span>|<span data-ttu-id="83b90-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="83b90-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="83b90-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="83b90-112">Description</span></span>  
 <span data-ttu-id="83b90-113">Indica que um aplicativo de fluxo de trabalho estiver ocioso e persistable.</span><span class="sxs-lookup"><span data-stu-id="83b90-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="83b90-114">O aplicativo de fluxo de trabalho será rodado em marcha lento ou persistente.</span><span class="sxs-lookup"><span data-stu-id="83b90-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="83b90-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="83b90-115">Message</span></span>  
 <span data-ttu-id="83b90-116">WorkflowApplication Id: '%1' está ociosa e persistente.</span><span class="sxs-lookup"><span data-stu-id="83b90-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="83b90-117">A seguinte ação será tomada: %2.</span><span class="sxs-lookup"><span data-stu-id="83b90-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="83b90-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="83b90-118">Details</span></span>  
  
|<span data-ttu-id="83b90-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="83b90-119">Data Item Name</span></span>|<span data-ttu-id="83b90-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="83b90-120">Data Item Type</span></span>|<span data-ttu-id="83b90-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="83b90-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="83b90-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="83b90-122">WorkflowApplicationId</span></span>|<span data-ttu-id="83b90-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="83b90-123">xs:string</span></span>|<span data-ttu-id="83b90-124">A identificação do aplicativo de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="83b90-124">The workflow application id</span></span>|  
|<span data-ttu-id="83b90-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="83b90-125">ActionTaken</span></span>|<span data-ttu-id="83b90-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="83b90-126">xs:string</span></span>|<span data-ttu-id="83b90-127">A ação a ser tomada no aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="83b90-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="83b90-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="83b90-128">AppDomain</span></span>|<span data-ttu-id="83b90-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="83b90-129">xs:string</span></span>|<span data-ttu-id="83b90-130">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="83b90-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
