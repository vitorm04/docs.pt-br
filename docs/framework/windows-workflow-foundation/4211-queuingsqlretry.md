---
title: 4211 - QueuingSqlRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 349a91f5b4708d829aee8d7f055871ac7dcc8914
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="ddb60-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="ddb60-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="ddb60-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ddb60-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ddb60-104">ID</span><span class="sxs-lookup"><span data-stu-id="ddb60-104">ID</span></span>|<span data-ttu-id="ddb60-105">4211</span><span class="sxs-lookup"><span data-stu-id="ddb60-105">4211</span></span>|  
|<span data-ttu-id="ddb60-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="ddb60-106">Keywords</span></span>|<span data-ttu-id="ddb60-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="ddb60-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="ddb60-108">Nível</span><span class="sxs-lookup"><span data-stu-id="ddb60-108">Level</span></span>|<span data-ttu-id="ddb60-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="ddb60-109">Warning</span></span>|  
|<span data-ttu-id="ddb60-110">Canal</span><span class="sxs-lookup"><span data-stu-id="ddb60-110">Channel</span></span>|<span data-ttu-id="ddb60-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="ddb60-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ddb60-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ddb60-112">Description</span></span>  
 <span data-ttu-id="ddb60-113">Indica a nova tentativa de enfileiramento SQL.</span><span class="sxs-lookup"><span data-stu-id="ddb60-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ddb60-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="ddb60-114">Message</span></span>  
 <span data-ttu-id="ddb60-115">Nova tentativa SQL fila com atraso %1 milissegundos.</span><span class="sxs-lookup"><span data-stu-id="ddb60-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ddb60-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ddb60-116">Details</span></span>  
  
|<span data-ttu-id="ddb60-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="ddb60-117">Data Item Name</span></span>|<span data-ttu-id="ddb60-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="ddb60-118">Data Item Type</span></span>|<span data-ttu-id="ddb60-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ddb60-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ddb60-120">Atraso</span><span class="sxs-lookup"><span data-stu-id="ddb60-120">Delay</span></span>|<span data-ttu-id="ddb60-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ddb60-121">xs:string</span></span>|<span data-ttu-id="ddb60-122">O atraso entre o tenta.</span><span class="sxs-lookup"><span data-stu-id="ddb60-122">The delay between retries.</span></span>|  
|<span data-ttu-id="ddb60-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ddb60-123">AppDomain</span></span>|<span data-ttu-id="ddb60-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ddb60-124">xs:string</span></span>|<span data-ttu-id="ddb60-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ddb60-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
