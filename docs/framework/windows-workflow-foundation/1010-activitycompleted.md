---
title: 1010 - ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: 355281e6aa8f621bd2f9c0862e641fafec872750
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509691"
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="43eab-102">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="43eab-102">1010 - ActivityCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="43eab-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="43eab-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="43eab-104">ID</span><span class="sxs-lookup"><span data-stu-id="43eab-104">ID</span></span>|<span data-ttu-id="43eab-105">1010</span><span class="sxs-lookup"><span data-stu-id="43eab-105">1010</span></span>|  
|<span data-ttu-id="43eab-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="43eab-106">Keywords</span></span>|<span data-ttu-id="43eab-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="43eab-107">WFRuntime</span></span>|  
|<span data-ttu-id="43eab-108">Nível</span><span class="sxs-lookup"><span data-stu-id="43eab-108">Level</span></span>|<span data-ttu-id="43eab-109">Informações</span><span class="sxs-lookup"><span data-stu-id="43eab-109">Information</span></span>|  
|<span data-ttu-id="43eab-110">Canal</span><span class="sxs-lookup"><span data-stu-id="43eab-110">Channel</span></span>|<span data-ttu-id="43eab-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="43eab-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="43eab-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="43eab-112">Description</span></span>  
 <span data-ttu-id="43eab-113">Indica que uma atividade concluiu a execução.</span><span class="sxs-lookup"><span data-stu-id="43eab-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="43eab-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="43eab-114">Message</span></span>  
 <span data-ttu-id="43eab-115">Atividade “%1", DisplayName: “%2", InstanceId: “%3 concluíram " em “%4 " estado.</span><span class="sxs-lookup"><span data-stu-id="43eab-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="43eab-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="43eab-116">Details</span></span>  
  
|<span data-ttu-id="43eab-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="43eab-117">Data Item Name</span></span>|<span data-ttu-id="43eab-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="43eab-118">Data Item Type</span></span>|<span data-ttu-id="43eab-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="43eab-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="43eab-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="43eab-120">Activity</span></span>|<span data-ttu-id="43eab-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="43eab-121">xs:string</span></span>|<span data-ttu-id="43eab-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="43eab-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="43eab-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="43eab-123">DisplayName</span></span>|<span data-ttu-id="43eab-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="43eab-124">xs:string</span></span>|<span data-ttu-id="43eab-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="43eab-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="43eab-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="43eab-126">InstanceId</span></span>|<span data-ttu-id="43eab-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="43eab-127">xs:string</span></span>|<span data-ttu-id="43eab-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="43eab-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="43eab-129">Estado</span><span class="sxs-lookup"><span data-stu-id="43eab-129">State</span></span>|<span data-ttu-id="43eab-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="43eab-130">xs:string</span></span>|<span data-ttu-id="43eab-131">O estado da atividade.</span><span class="sxs-lookup"><span data-stu-id="43eab-131">The state of the activity.</span></span>|  
|<span data-ttu-id="43eab-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="43eab-132">AppDomain</span></span>|<span data-ttu-id="43eab-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="43eab-133">xs:string</span></span>|<span data-ttu-id="43eab-134">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="43eab-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
