---
title: 1013 - CompleteExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: de9add3f537c1d8ff97c92892197598bcc7a4fe7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="47eda-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="47eda-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="47eda-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="47eda-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="47eda-104">ID</span><span class="sxs-lookup"><span data-stu-id="47eda-104">ID</span></span>|<span data-ttu-id="47eda-105">1013</span><span class="sxs-lookup"><span data-stu-id="47eda-105">1013</span></span>|  
|<span data-ttu-id="47eda-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="47eda-106">Keywords</span></span>|<span data-ttu-id="47eda-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="47eda-107">WFRuntime</span></span>|  
|<span data-ttu-id="47eda-108">Nível</span><span class="sxs-lookup"><span data-stu-id="47eda-108">Level</span></span>|<span data-ttu-id="47eda-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="47eda-109">Verbose</span></span>|  
|<span data-ttu-id="47eda-110">Canal</span><span class="sxs-lookup"><span data-stu-id="47eda-110">Channel</span></span>|<span data-ttu-id="47eda-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="47eda-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="47eda-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="47eda-112">Description</span></span>  
 <span data-ttu-id="47eda-113">Indica que um ExecuteActivityWorkItem concluiu</span><span class="sxs-lookup"><span data-stu-id="47eda-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="47eda-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="47eda-114">Message</span></span>  
 <span data-ttu-id="47eda-115">Um ExecuteActivityWorkItem concluiu para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="47eda-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="47eda-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="47eda-116">Details</span></span>  
  
|<span data-ttu-id="47eda-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="47eda-117">Data Item Name</span></span>|<span data-ttu-id="47eda-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="47eda-118">Data Item Type</span></span>|<span data-ttu-id="47eda-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="47eda-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="47eda-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="47eda-120">Activity</span></span>|<span data-ttu-id="47eda-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="47eda-121">xs:string</span></span>|<span data-ttu-id="47eda-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="47eda-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="47eda-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="47eda-123">DisplayName</span></span>|<span data-ttu-id="47eda-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="47eda-124">xs:string</span></span>|<span data-ttu-id="47eda-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="47eda-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="47eda-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="47eda-126">InstanceId</span></span>|<span data-ttu-id="47eda-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="47eda-127">xs:string</span></span>|<span data-ttu-id="47eda-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="47eda-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="47eda-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="47eda-129">AppDomain</span></span>|<span data-ttu-id="47eda-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="47eda-130">xs:string</span></span>|<span data-ttu-id="47eda-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="47eda-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
