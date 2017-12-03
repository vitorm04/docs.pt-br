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
ms.openlocfilehash: a5fb800718c1fd231d0cd02bf015333a44fa794f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="37c15-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="37c15-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="37c15-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="37c15-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="37c15-104">ID</span><span class="sxs-lookup"><span data-stu-id="37c15-104">ID</span></span>|<span data-ttu-id="37c15-105">1026</span><span class="sxs-lookup"><span data-stu-id="37c15-105">1026</span></span>|  
|<span data-ttu-id="37c15-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="37c15-106">Keywords</span></span>|<span data-ttu-id="37c15-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="37c15-107">WFRuntime</span></span>|  
|<span data-ttu-id="37c15-108">Nível</span><span class="sxs-lookup"><span data-stu-id="37c15-108">Level</span></span>|<span data-ttu-id="37c15-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="37c15-109">Verbose</span></span>|  
|<span data-ttu-id="37c15-110">Canal</span><span class="sxs-lookup"><span data-stu-id="37c15-110">Channel</span></span>|<span data-ttu-id="37c15-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="37c15-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="37c15-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="37c15-112">Description</span></span>  
 <span data-ttu-id="37c15-113">Indica que um TransactionContextWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="37c15-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="37c15-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="37c15-114">Message</span></span>  
 <span data-ttu-id="37c15-115">Um TransactionContextWorkItem foi agendada para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="37c15-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="37c15-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="37c15-116">Details</span></span>  
  
|<span data-ttu-id="37c15-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="37c15-117">Data Item Name</span></span>|<span data-ttu-id="37c15-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="37c15-118">Data Item Type</span></span>|<span data-ttu-id="37c15-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="37c15-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="37c15-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="37c15-120">Activity</span></span>|<span data-ttu-id="37c15-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="37c15-121">xs:string</span></span>|<span data-ttu-id="37c15-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="37c15-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="37c15-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="37c15-123">DisplayName</span></span>|<span data-ttu-id="37c15-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="37c15-124">xs:string</span></span>|<span data-ttu-id="37c15-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="37c15-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="37c15-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="37c15-126">InstanceId</span></span>|<span data-ttu-id="37c15-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="37c15-127">xs:string</span></span>|<span data-ttu-id="37c15-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="37c15-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="37c15-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="37c15-129">AppDomain</span></span>|<span data-ttu-id="37c15-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="37c15-130">xs:string</span></span>|<span data-ttu-id="37c15-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="37c15-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
