---
title: 1033 - StartRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2cc905fbd960b3ed5c36cac40300ba58697f8903
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="e2087-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="e2087-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e2087-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e2087-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e2087-104">ID</span><span class="sxs-lookup"><span data-stu-id="e2087-104">ID</span></span>|<span data-ttu-id="e2087-105">1033</span><span class="sxs-lookup"><span data-stu-id="e2087-105">1033</span></span>|  
|<span data-ttu-id="e2087-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="e2087-106">Keywords</span></span>|<span data-ttu-id="e2087-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e2087-107">WFRuntime</span></span>|  
|<span data-ttu-id="e2087-108">Nível</span><span class="sxs-lookup"><span data-stu-id="e2087-108">Level</span></span>|<span data-ttu-id="e2087-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="e2087-109">Verbose</span></span>|  
|<span data-ttu-id="e2087-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e2087-110">Channel</span></span>|<span data-ttu-id="e2087-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="e2087-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e2087-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2087-112">Description</span></span>  
 <span data-ttu-id="e2087-113">Indica que um RuntimeWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="e2087-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e2087-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="e2087-114">Message</span></span>  
 <span data-ttu-id="e2087-115">Iniciar a execução de um item de trabalho de tempo de execução para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="e2087-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e2087-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e2087-116">Details</span></span>  
  
|<span data-ttu-id="e2087-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="e2087-117">Data Item Name</span></span>|<span data-ttu-id="e2087-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="e2087-118">Data Item Type</span></span>|<span data-ttu-id="e2087-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2087-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e2087-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="e2087-120">Activity</span></span>|<span data-ttu-id="e2087-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2087-121">xs:string</span></span>|<span data-ttu-id="e2087-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="e2087-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="e2087-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e2087-123">DisplayName</span></span>|<span data-ttu-id="e2087-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2087-124">xs:string</span></span>|<span data-ttu-id="e2087-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="e2087-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="e2087-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e2087-126">InstanceId</span></span>|<span data-ttu-id="e2087-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2087-127">xs:string</span></span>|<span data-ttu-id="e2087-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="e2087-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e2087-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e2087-129">AppDomain</span></span>|<span data-ttu-id="e2087-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2087-130">xs:string</span></span>|<span data-ttu-id="e2087-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e2087-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
