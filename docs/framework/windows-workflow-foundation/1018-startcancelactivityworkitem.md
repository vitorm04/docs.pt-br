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
ms.openlocfilehash: b64ea860e9881ed31aa0d8e78dec55f329cc6fad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="7f694-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="7f694-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="7f694-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7f694-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7f694-104">ID</span><span class="sxs-lookup"><span data-stu-id="7f694-104">ID</span></span>|<span data-ttu-id="7f694-105">1018</span><span class="sxs-lookup"><span data-stu-id="7f694-105">1018</span></span>|  
|<span data-ttu-id="7f694-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="7f694-106">Keywords</span></span>|<span data-ttu-id="7f694-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7f694-107">WFRuntime</span></span>|  
|<span data-ttu-id="7f694-108">Nível</span><span class="sxs-lookup"><span data-stu-id="7f694-108">Level</span></span>|<span data-ttu-id="7f694-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="7f694-109">Verbose</span></span>|  
|<span data-ttu-id="7f694-110">Canal</span><span class="sxs-lookup"><span data-stu-id="7f694-110">Channel</span></span>|<span data-ttu-id="7f694-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="7f694-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7f694-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f694-112">Description</span></span>  
 <span data-ttu-id="7f694-113">Indica que um CancelActivityWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="7f694-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7f694-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="7f694-114">Message</span></span>  
 <span data-ttu-id="7f694-115">Iniciar a execução de um CancelActivityWorkItem para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="7f694-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7f694-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7f694-116">Details</span></span>  
  
|<span data-ttu-id="7f694-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="7f694-117">Data Item Name</span></span>|<span data-ttu-id="7f694-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="7f694-118">Data Item Type</span></span>|<span data-ttu-id="7f694-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f694-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7f694-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="7f694-120">Activity</span></span>|<span data-ttu-id="7f694-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f694-121">xs:string</span></span>|<span data-ttu-id="7f694-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="7f694-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="7f694-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7f694-123">DisplayName</span></span>|<span data-ttu-id="7f694-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f694-124">xs:string</span></span>|<span data-ttu-id="7f694-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="7f694-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="7f694-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="7f694-126">InstanceId</span></span>|<span data-ttu-id="7f694-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f694-127">xs:string</span></span>|<span data-ttu-id="7f694-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="7f694-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="7f694-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7f694-129">AppDomain</span></span>|<span data-ttu-id="7f694-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f694-130">xs:string</span></span>|<span data-ttu-id="7f694-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7f694-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
