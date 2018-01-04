---
title: 1028 - CompleteTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cd2ee443d6c521f168a170a1079eb4e9657e2dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="8730a-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="8730a-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="8730a-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8730a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8730a-104">ID</span><span class="sxs-lookup"><span data-stu-id="8730a-104">ID</span></span>|<span data-ttu-id="8730a-105">1028</span><span class="sxs-lookup"><span data-stu-id="8730a-105">1028</span></span>|  
|<span data-ttu-id="8730a-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="8730a-106">Keywords</span></span>|<span data-ttu-id="8730a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8730a-107">WFRuntime</span></span>|  
|<span data-ttu-id="8730a-108">Nível</span><span class="sxs-lookup"><span data-stu-id="8730a-108">Level</span></span>|<span data-ttu-id="8730a-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="8730a-109">Verbose</span></span>|  
|<span data-ttu-id="8730a-110">Canal</span><span class="sxs-lookup"><span data-stu-id="8730a-110">Channel</span></span>|<span data-ttu-id="8730a-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="8730a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8730a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8730a-112">Description</span></span>  
 <span data-ttu-id="8730a-113">Indica que um TransactionContextWorkItem terminado.</span><span class="sxs-lookup"><span data-stu-id="8730a-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8730a-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="8730a-114">Message</span></span>  
 <span data-ttu-id="8730a-115">Um TransactionContextWorkItem concluiu para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="8730a-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8730a-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8730a-116">Details</span></span>  
  
|<span data-ttu-id="8730a-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="8730a-117">Data Item Name</span></span>|<span data-ttu-id="8730a-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="8730a-118">Data Item Type</span></span>|<span data-ttu-id="8730a-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="8730a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8730a-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="8730a-120">Activity</span></span>|<span data-ttu-id="8730a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8730a-121">xs:string</span></span>|<span data-ttu-id="8730a-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="8730a-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="8730a-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8730a-123">DisplayName</span></span>|<span data-ttu-id="8730a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8730a-124">xs:string</span></span>|<span data-ttu-id="8730a-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="8730a-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="8730a-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="8730a-126">InstanceId</span></span>|<span data-ttu-id="8730a-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="8730a-127">xs:string</span></span>|<span data-ttu-id="8730a-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="8730a-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="8730a-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8730a-129">AppDomain</span></span>|<span data-ttu-id="8730a-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="8730a-130">xs:string</span></span>|<span data-ttu-id="8730a-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8730a-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
