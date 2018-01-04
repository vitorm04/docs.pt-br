---
title: 3508 - TrackingProfileNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34812b6ddefb69c053cfefa91d7227a7bf15f42e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="d38a4-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="d38a4-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="d38a4-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d38a4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d38a4-104">ID</span><span class="sxs-lookup"><span data-stu-id="d38a4-104">ID</span></span>|<span data-ttu-id="d38a4-105">3508</span><span class="sxs-lookup"><span data-stu-id="d38a4-105">3508</span></span>|  
|<span data-ttu-id="d38a4-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="d38a4-106">Keywords</span></span>|<span data-ttu-id="d38a4-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="d38a4-107">WFServices</span></span>|  
|<span data-ttu-id="d38a4-108">Nível</span><span class="sxs-lookup"><span data-stu-id="d38a4-108">Level</span></span>|<span data-ttu-id="d38a4-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="d38a4-109">Verbose</span></span>|  
|<span data-ttu-id="d38a4-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d38a4-110">Channel</span></span>|<span data-ttu-id="d38a4-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="d38a4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d38a4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d38a4-112">Description</span></span>  
 <span data-ttu-id="d38a4-113">Indica que um ou TrackingProfile não está localizado no arquivo de configuração ou o ActivityDefinitionId não corresponde ao perfil.</span><span class="sxs-lookup"><span data-stu-id="d38a4-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d38a4-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d38a4-114">Message</span></span>  
 <span data-ttu-id="d38a4-115">TrackingProfile “%1 " para o ActivityDefinitionId “%2 " não encontrado.</span><span class="sxs-lookup"><span data-stu-id="d38a4-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="d38a4-116">O TrackingProfile não é encontrado no arquivo de configuração ou a ActivityDefinitionId não é correspondente.</span><span class="sxs-lookup"><span data-stu-id="d38a4-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d38a4-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d38a4-117">Details</span></span>  
  
|<span data-ttu-id="d38a4-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="d38a4-118">Data Item Name</span></span>|<span data-ttu-id="d38a4-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="d38a4-119">Data Item Type</span></span>|<span data-ttu-id="d38a4-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="d38a4-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d38a4-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="d38a4-121">TrackingProfile</span></span>|<span data-ttu-id="d38a4-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="d38a4-122">xs:string</span></span>|<span data-ttu-id="d38a4-123">O nome de perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d38a4-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="d38a4-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="d38a4-124">ActivityDefinitionId</span></span>|<span data-ttu-id="d38a4-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="d38a4-125">xs:string</span></span>|<span data-ttu-id="d38a4-126">A identificação da definição de atividades</span><span class="sxs-lookup"><span data-stu-id="d38a4-126">The activity definition id.</span></span>|  
|<span data-ttu-id="d38a4-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d38a4-127">AppDomain</span></span>|<span data-ttu-id="d38a4-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="d38a4-128">xs:string</span></span>|<span data-ttu-id="d38a4-129">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d38a4-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
