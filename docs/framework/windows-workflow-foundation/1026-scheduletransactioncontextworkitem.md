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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d881f1be4e809cf45f100b966d6013ae8fa88f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="f6de2-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="f6de2-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="f6de2-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f6de2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f6de2-104">ID</span><span class="sxs-lookup"><span data-stu-id="f6de2-104">ID</span></span>|<span data-ttu-id="f6de2-105">1026</span><span class="sxs-lookup"><span data-stu-id="f6de2-105">1026</span></span>|  
|<span data-ttu-id="f6de2-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="f6de2-106">Keywords</span></span>|<span data-ttu-id="f6de2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f6de2-107">WFRuntime</span></span>|  
|<span data-ttu-id="f6de2-108">Nível</span><span class="sxs-lookup"><span data-stu-id="f6de2-108">Level</span></span>|<span data-ttu-id="f6de2-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="f6de2-109">Verbose</span></span>|  
|<span data-ttu-id="f6de2-110">Canal</span><span class="sxs-lookup"><span data-stu-id="f6de2-110">Channel</span></span>|<span data-ttu-id="f6de2-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="f6de2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f6de2-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6de2-112">Description</span></span>  
 <span data-ttu-id="f6de2-113">Indica que um TransactionContextWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="f6de2-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f6de2-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="f6de2-114">Message</span></span>  
 <span data-ttu-id="f6de2-115">Um TransactionContextWorkItem foi agendada para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="f6de2-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f6de2-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f6de2-116">Details</span></span>  
  
|<span data-ttu-id="f6de2-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="f6de2-117">Data Item Name</span></span>|<span data-ttu-id="f6de2-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="f6de2-118">Data Item Type</span></span>|<span data-ttu-id="f6de2-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6de2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f6de2-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="f6de2-120">Activity</span></span>|<span data-ttu-id="f6de2-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6de2-121">xs:string</span></span>|<span data-ttu-id="f6de2-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="f6de2-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="f6de2-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f6de2-123">DisplayName</span></span>|<span data-ttu-id="f6de2-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6de2-124">xs:string</span></span>|<span data-ttu-id="f6de2-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="f6de2-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="f6de2-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="f6de2-126">InstanceId</span></span>|<span data-ttu-id="f6de2-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6de2-127">xs:string</span></span>|<span data-ttu-id="f6de2-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="f6de2-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="f6de2-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f6de2-129">AppDomain</span></span>|<span data-ttu-id="f6de2-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6de2-130">xs:string</span></span>|<span data-ttu-id="f6de2-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f6de2-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
