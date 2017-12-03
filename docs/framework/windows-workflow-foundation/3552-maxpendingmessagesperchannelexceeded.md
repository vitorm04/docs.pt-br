---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5455472a5b9ebdba7aea7d0384ce9cd4a9a2849d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="fa400-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="fa400-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="fa400-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="fa400-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa400-104">ID</span><span class="sxs-lookup"><span data-stu-id="fa400-104">ID</span></span>|<span data-ttu-id="fa400-105">3552</span><span class="sxs-lookup"><span data-stu-id="fa400-105">3552</span></span>|  
|<span data-ttu-id="fa400-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="fa400-106">Keywords</span></span>|<span data-ttu-id="fa400-107">Cota, WFServices</span><span class="sxs-lookup"><span data-stu-id="fa400-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="fa400-108">Nível</span><span class="sxs-lookup"><span data-stu-id="fa400-108">Level</span></span>|<span data-ttu-id="fa400-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="fa400-109">Warning</span></span>|  
|<span data-ttu-id="fa400-110">Canal</span><span class="sxs-lookup"><span data-stu-id="fa400-110">Channel</span></span>|<span data-ttu-id="fa400-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="fa400-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fa400-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa400-112">Description</span></span>  
 <span data-ttu-id="fa400-113">Indica que o limite de “MaxPendingMessagesPerChannel” de regulador de pressão foi atingido.</span><span class="sxs-lookup"><span data-stu-id="fa400-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fa400-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="fa400-114">Message</span></span>  
 <span data-ttu-id="fa400-115">Foi atingido o limite 'MaxPendingMessagesPerChannel' de '%1' do acelerador.</span><span class="sxs-lookup"><span data-stu-id="fa400-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="fa400-116">Para aumentar esse limite, ajuste a propriedade MaxPendingMessagesPerChannel no BufferedReceiveServiceBehavior.</span><span class="sxs-lookup"><span data-stu-id="fa400-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fa400-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="fa400-117">Details</span></span>  
  
|<span data-ttu-id="fa400-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="fa400-118">Data Item Name</span></span>|<span data-ttu-id="fa400-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="fa400-119">Data Item Type</span></span>|<span data-ttu-id="fa400-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa400-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fa400-121">Limite</span><span class="sxs-lookup"><span data-stu-id="fa400-121">Limit</span></span>|<span data-ttu-id="fa400-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="fa400-122">xs:string</span></span>|<span data-ttu-id="fa400-123">O limite de regulador de pressão de MaxPendingMessagesPerChannel.</span><span class="sxs-lookup"><span data-stu-id="fa400-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="fa400-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fa400-124">AppDomain</span></span>|<span data-ttu-id="fa400-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="fa400-125">xs:string</span></span>|<span data-ttu-id="fa400-126">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fa400-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
