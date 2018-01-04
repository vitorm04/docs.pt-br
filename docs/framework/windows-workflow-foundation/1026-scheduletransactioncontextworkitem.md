---
title: 1026 - ScheduleTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83c99ddf9c5d4a8fa468303fb198abc349ace6d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="af62e-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="af62e-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="af62e-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="af62e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="af62e-104">ID</span><span class="sxs-lookup"><span data-stu-id="af62e-104">ID</span></span>|<span data-ttu-id="af62e-105">1026</span><span class="sxs-lookup"><span data-stu-id="af62e-105">1026</span></span>|  
|<span data-ttu-id="af62e-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="af62e-106">Keywords</span></span>|<span data-ttu-id="af62e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="af62e-107">WFRuntime</span></span>|  
|<span data-ttu-id="af62e-108">Nível</span><span class="sxs-lookup"><span data-stu-id="af62e-108">Level</span></span>|<span data-ttu-id="af62e-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="af62e-109">Verbose</span></span>|  
|<span data-ttu-id="af62e-110">Canal</span><span class="sxs-lookup"><span data-stu-id="af62e-110">Channel</span></span>|<span data-ttu-id="af62e-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="af62e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="af62e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="af62e-112">Description</span></span>  
 <span data-ttu-id="af62e-113">Indica que um TransactionContextWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="af62e-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="af62e-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="af62e-114">Message</span></span>  
 <span data-ttu-id="af62e-115">Um TransactionContextWorkItem foi agendada para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="af62e-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="af62e-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="af62e-116">Details</span></span>  
  
|<span data-ttu-id="af62e-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="af62e-117">Data Item Name</span></span>|<span data-ttu-id="af62e-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="af62e-118">Data Item Type</span></span>|<span data-ttu-id="af62e-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="af62e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="af62e-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="af62e-120">Activity</span></span>|<span data-ttu-id="af62e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="af62e-121">xs:string</span></span>|<span data-ttu-id="af62e-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="af62e-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="af62e-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="af62e-123">DisplayName</span></span>|<span data-ttu-id="af62e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="af62e-124">xs:string</span></span>|<span data-ttu-id="af62e-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="af62e-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="af62e-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="af62e-126">InstanceId</span></span>|<span data-ttu-id="af62e-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="af62e-127">xs:string</span></span>|<span data-ttu-id="af62e-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="af62e-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="af62e-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="af62e-129">AppDomain</span></span>|<span data-ttu-id="af62e-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="af62e-130">xs:string</span></span>|<span data-ttu-id="af62e-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="af62e-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
