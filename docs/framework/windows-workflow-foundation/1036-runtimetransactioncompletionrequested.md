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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4f497d777221a98b38603b2ced29342651b1020b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="4600c-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="4600c-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="4600c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4600c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4600c-104">ID</span><span class="sxs-lookup"><span data-stu-id="4600c-104">ID</span></span>|<span data-ttu-id="4600c-105">1036</span><span class="sxs-lookup"><span data-stu-id="4600c-105">1036</span></span>|  
|<span data-ttu-id="4600c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="4600c-106">Keywords</span></span>|<span data-ttu-id="4600c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4600c-107">WFRuntime</span></span>|  
|<span data-ttu-id="4600c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="4600c-108">Level</span></span>|<span data-ttu-id="4600c-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="4600c-109">Verbose</span></span>|  
|<span data-ttu-id="4600c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="4600c-110">Channel</span></span>|<span data-ttu-id="4600c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="4600c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4600c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4600c-112">Description</span></span>  
 <span data-ttu-id="4600c-113">Indica que uma atividade agendou a conclusão de transação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4600c-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4600c-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="4600c-114">Message</span></span>  
 <span data-ttu-id="4600c-115">Atividade “%1", DisplayName: “%2", InstanceId: “%3 " agendaram a conclusão de transação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4600c-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4600c-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4600c-116">Details</span></span>  
  
|<span data-ttu-id="4600c-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="4600c-117">Data Item Name</span></span>|<span data-ttu-id="4600c-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="4600c-118">Data Item Type</span></span>|<span data-ttu-id="4600c-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="4600c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4600c-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="4600c-120">Activity</span></span>|<span data-ttu-id="4600c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="4600c-121">xs:string</span></span>|<span data-ttu-id="4600c-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="4600c-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="4600c-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4600c-123">DisplayName</span></span>|<span data-ttu-id="4600c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="4600c-124">xs:string</span></span>|<span data-ttu-id="4600c-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="4600c-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="4600c-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4600c-126">InstanceId</span></span>|<span data-ttu-id="4600c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="4600c-127">xs:string</span></span>|<span data-ttu-id="4600c-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="4600c-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4600c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4600c-129">AppDomain</span></span>|<span data-ttu-id="4600c-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="4600c-130">xs:string</span></span>|<span data-ttu-id="4600c-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4600c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
