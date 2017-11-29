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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77ef22bd29c167b5be26ceb5360397d38c547c22
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="295aa-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="295aa-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="295aa-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="295aa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="295aa-104">ID</span><span class="sxs-lookup"><span data-stu-id="295aa-104">ID</span></span>|<span data-ttu-id="295aa-105">1028</span><span class="sxs-lookup"><span data-stu-id="295aa-105">1028</span></span>|  
|<span data-ttu-id="295aa-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="295aa-106">Keywords</span></span>|<span data-ttu-id="295aa-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="295aa-107">WFRuntime</span></span>|  
|<span data-ttu-id="295aa-108">Nível</span><span class="sxs-lookup"><span data-stu-id="295aa-108">Level</span></span>|<span data-ttu-id="295aa-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="295aa-109">Verbose</span></span>|  
|<span data-ttu-id="295aa-110">Canal</span><span class="sxs-lookup"><span data-stu-id="295aa-110">Channel</span></span>|<span data-ttu-id="295aa-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="295aa-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="295aa-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="295aa-112">Description</span></span>  
 <span data-ttu-id="295aa-113">Indica que um TransactionContextWorkItem terminado.</span><span class="sxs-lookup"><span data-stu-id="295aa-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="295aa-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="295aa-114">Message</span></span>  
 <span data-ttu-id="295aa-115">Um TransactionContextWorkItem concluiu para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="295aa-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="295aa-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="295aa-116">Details</span></span>  
  
|<span data-ttu-id="295aa-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="295aa-117">Data Item Name</span></span>|<span data-ttu-id="295aa-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="295aa-118">Data Item Type</span></span>|<span data-ttu-id="295aa-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="295aa-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="295aa-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="295aa-120">Activity</span></span>|<span data-ttu-id="295aa-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="295aa-121">xs:string</span></span>|<span data-ttu-id="295aa-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="295aa-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="295aa-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="295aa-123">DisplayName</span></span>|<span data-ttu-id="295aa-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="295aa-124">xs:string</span></span>|<span data-ttu-id="295aa-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="295aa-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="295aa-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="295aa-126">InstanceId</span></span>|<span data-ttu-id="295aa-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="295aa-127">xs:string</span></span>|<span data-ttu-id="295aa-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="295aa-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="295aa-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="295aa-129">AppDomain</span></span>|<span data-ttu-id="295aa-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="295aa-130">xs:string</span></span>|<span data-ttu-id="295aa-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="295aa-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
