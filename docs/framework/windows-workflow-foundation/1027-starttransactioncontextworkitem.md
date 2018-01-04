---
title: 1027 - StartTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: baa644cb7693b8608f119cf211b3b08ab4b1a2b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="dd32c-102">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="dd32c-102">1027 - StartTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="dd32c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="dd32c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dd32c-104">ID</span><span class="sxs-lookup"><span data-stu-id="dd32c-104">ID</span></span>|<span data-ttu-id="dd32c-105">1027</span><span class="sxs-lookup"><span data-stu-id="dd32c-105">1027</span></span>|  
|<span data-ttu-id="dd32c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="dd32c-106">Keywords</span></span>|<span data-ttu-id="dd32c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="dd32c-107">WFRuntime</span></span>|  
|<span data-ttu-id="dd32c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="dd32c-108">Level</span></span>|<span data-ttu-id="dd32c-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="dd32c-109">Verbose</span></span>|  
|<span data-ttu-id="dd32c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="dd32c-110">Channel</span></span>|<span data-ttu-id="dd32c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="dd32c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dd32c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd32c-112">Description</span></span>  
 <span data-ttu-id="dd32c-113">Indica que um TransactionContextWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="dd32c-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dd32c-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="dd32c-114">Message</span></span>  
 <span data-ttu-id="dd32c-115">Iniciar a execução de um TransactionContextWorkItem para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="dd32c-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dd32c-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="dd32c-116">Details</span></span>  
  
|<span data-ttu-id="dd32c-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="dd32c-117">Data Item Name</span></span>|<span data-ttu-id="dd32c-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="dd32c-118">Data Item Type</span></span>|<span data-ttu-id="dd32c-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd32c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dd32c-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="dd32c-120">Activity</span></span>|<span data-ttu-id="dd32c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="dd32c-121">xs:string</span></span>|<span data-ttu-id="dd32c-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="dd32c-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="dd32c-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="dd32c-123">DisplayName</span></span>|<span data-ttu-id="dd32c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="dd32c-124">xs:string</span></span>|<span data-ttu-id="dd32c-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="dd32c-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="dd32c-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="dd32c-126">InstanceId</span></span>|<span data-ttu-id="dd32c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="dd32c-127">xs:string</span></span>|<span data-ttu-id="dd32c-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="dd32c-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="dd32c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dd32c-129">AppDomain</span></span>|<span data-ttu-id="dd32c-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="dd32c-130">xs:string</span></span>|<span data-ttu-id="dd32c-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="dd32c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
