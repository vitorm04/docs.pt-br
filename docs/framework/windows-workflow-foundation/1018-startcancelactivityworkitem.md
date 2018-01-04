---
title: 1018 - StartCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d64d18474ff867ee5679e07c18a288f07185f60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="493e8-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="493e8-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="493e8-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="493e8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="493e8-104">ID</span><span class="sxs-lookup"><span data-stu-id="493e8-104">ID</span></span>|<span data-ttu-id="493e8-105">1018</span><span class="sxs-lookup"><span data-stu-id="493e8-105">1018</span></span>|  
|<span data-ttu-id="493e8-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="493e8-106">Keywords</span></span>|<span data-ttu-id="493e8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="493e8-107">WFRuntime</span></span>|  
|<span data-ttu-id="493e8-108">Nível</span><span class="sxs-lookup"><span data-stu-id="493e8-108">Level</span></span>|<span data-ttu-id="493e8-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="493e8-109">Verbose</span></span>|  
|<span data-ttu-id="493e8-110">Canal</span><span class="sxs-lookup"><span data-stu-id="493e8-110">Channel</span></span>|<span data-ttu-id="493e8-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="493e8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="493e8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="493e8-112">Description</span></span>  
 <span data-ttu-id="493e8-113">Indica que um CancelActivityWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="493e8-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="493e8-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="493e8-114">Message</span></span>  
 <span data-ttu-id="493e8-115">Iniciar a execução de um CancelActivityWorkItem para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="493e8-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="493e8-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="493e8-116">Details</span></span>  
  
|<span data-ttu-id="493e8-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="493e8-117">Data Item Name</span></span>|<span data-ttu-id="493e8-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="493e8-118">Data Item Type</span></span>|<span data-ttu-id="493e8-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="493e8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="493e8-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="493e8-120">Activity</span></span>|<span data-ttu-id="493e8-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="493e8-121">xs:string</span></span>|<span data-ttu-id="493e8-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="493e8-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="493e8-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="493e8-123">DisplayName</span></span>|<span data-ttu-id="493e8-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="493e8-124">xs:string</span></span>|<span data-ttu-id="493e8-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="493e8-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="493e8-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="493e8-126">InstanceId</span></span>|<span data-ttu-id="493e8-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="493e8-127">xs:string</span></span>|<span data-ttu-id="493e8-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="493e8-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="493e8-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="493e8-129">AppDomain</span></span>|<span data-ttu-id="493e8-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="493e8-130">xs:string</span></span>|<span data-ttu-id="493e8-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="493e8-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
