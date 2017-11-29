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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0de8e45a592cae49060f976b28a7a7bcf8781265
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="0875d-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="0875d-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="0875d-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0875d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0875d-104">ID</span><span class="sxs-lookup"><span data-stu-id="0875d-104">ID</span></span>|<span data-ttu-id="0875d-105">1033</span><span class="sxs-lookup"><span data-stu-id="0875d-105">1033</span></span>|  
|<span data-ttu-id="0875d-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="0875d-106">Keywords</span></span>|<span data-ttu-id="0875d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0875d-107">WFRuntime</span></span>|  
|<span data-ttu-id="0875d-108">Nível</span><span class="sxs-lookup"><span data-stu-id="0875d-108">Level</span></span>|<span data-ttu-id="0875d-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="0875d-109">Verbose</span></span>|  
|<span data-ttu-id="0875d-110">Canal</span><span class="sxs-lookup"><span data-stu-id="0875d-110">Channel</span></span>|<span data-ttu-id="0875d-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="0875d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0875d-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0875d-112">Description</span></span>  
 <span data-ttu-id="0875d-113">Indica que um RuntimeWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="0875d-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0875d-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="0875d-114">Message</span></span>  
 <span data-ttu-id="0875d-115">Iniciar a execução de um item de trabalho de tempo de execução para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="0875d-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0875d-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="0875d-116">Details</span></span>  
  
|<span data-ttu-id="0875d-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="0875d-117">Data Item Name</span></span>|<span data-ttu-id="0875d-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="0875d-118">Data Item Type</span></span>|<span data-ttu-id="0875d-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0875d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0875d-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="0875d-120">Activity</span></span>|<span data-ttu-id="0875d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="0875d-121">xs:string</span></span>|<span data-ttu-id="0875d-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="0875d-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="0875d-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="0875d-123">DisplayName</span></span>|<span data-ttu-id="0875d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="0875d-124">xs:string</span></span>|<span data-ttu-id="0875d-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="0875d-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="0875d-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="0875d-126">InstanceId</span></span>|<span data-ttu-id="0875d-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="0875d-127">xs:string</span></span>|<span data-ttu-id="0875d-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="0875d-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="0875d-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0875d-129">AppDomain</span></span>|<span data-ttu-id="0875d-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="0875d-130">xs:string</span></span>|<span data-ttu-id="0875d-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0875d-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
