---
title: 1036 - RuntimeTransactionCompletionRequested
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 91fcac0bdfe885051941d100f1a2c131c547f19e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="43d1a-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="43d1a-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="43d1a-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="43d1a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="43d1a-104">ID</span><span class="sxs-lookup"><span data-stu-id="43d1a-104">ID</span></span>|<span data-ttu-id="43d1a-105">1036</span><span class="sxs-lookup"><span data-stu-id="43d1a-105">1036</span></span>|  
|<span data-ttu-id="43d1a-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="43d1a-106">Keywords</span></span>|<span data-ttu-id="43d1a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="43d1a-107">WFRuntime</span></span>|  
|<span data-ttu-id="43d1a-108">Nível</span><span class="sxs-lookup"><span data-stu-id="43d1a-108">Level</span></span>|<span data-ttu-id="43d1a-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="43d1a-109">Verbose</span></span>|  
|<span data-ttu-id="43d1a-110">Canal</span><span class="sxs-lookup"><span data-stu-id="43d1a-110">Channel</span></span>|<span data-ttu-id="43d1a-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="43d1a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="43d1a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="43d1a-112">Description</span></span>  
 <span data-ttu-id="43d1a-113">Indica que uma atividade agendou a conclusão de transação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="43d1a-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="43d1a-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="43d1a-114">Message</span></span>  
 <span data-ttu-id="43d1a-115">Atividade “%1", DisplayName: “%2", InstanceId: “%3 " agendaram a conclusão de transação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="43d1a-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="43d1a-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="43d1a-116">Details</span></span>  
  
|<span data-ttu-id="43d1a-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="43d1a-117">Data Item Name</span></span>|<span data-ttu-id="43d1a-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="43d1a-118">Data Item Type</span></span>|<span data-ttu-id="43d1a-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="43d1a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="43d1a-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="43d1a-120">Activity</span></span>|<span data-ttu-id="43d1a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="43d1a-121">xs:string</span></span>|<span data-ttu-id="43d1a-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="43d1a-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="43d1a-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="43d1a-123">DisplayName</span></span>|<span data-ttu-id="43d1a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="43d1a-124">xs:string</span></span>|<span data-ttu-id="43d1a-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="43d1a-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="43d1a-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="43d1a-126">InstanceId</span></span>|<span data-ttu-id="43d1a-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="43d1a-127">xs:string</span></span>|<span data-ttu-id="43d1a-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="43d1a-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="43d1a-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="43d1a-129">AppDomain</span></span>|<span data-ttu-id="43d1a-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="43d1a-130">xs:string</span></span>|<span data-ttu-id="43d1a-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="43d1a-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
