---
title: 4212 - LockRetryTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abe1f560cc984551f069a75873a7e5545aec03cf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="d44a4-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="d44a4-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="d44a4-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d44a4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d44a4-104">ID</span><span class="sxs-lookup"><span data-stu-id="d44a4-104">ID</span></span>|<span data-ttu-id="d44a4-105">4212</span><span class="sxs-lookup"><span data-stu-id="d44a4-105">4212</span></span>|  
|<span data-ttu-id="d44a4-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="d44a4-106">Keywords</span></span>|<span data-ttu-id="d44a4-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="d44a4-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="d44a4-108">Nível</span><span class="sxs-lookup"><span data-stu-id="d44a4-108">Level</span></span>|<span data-ttu-id="d44a4-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="d44a4-109">Warning</span></span>|  
|<span data-ttu-id="d44a4-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d44a4-110">Channel</span></span>|<span data-ttu-id="d44a4-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="d44a4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d44a4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d44a4-112">Description</span></span>  
 <span data-ttu-id="d44a4-113">O provedor SQL após um tempo limite tentar obter o bloqueio de instância.</span><span class="sxs-lookup"><span data-stu-id="d44a4-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d44a4-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d44a4-114">Message</span></span>  
 <span data-ttu-id="d44a4-115">Tempo limite está tentando adquirir o bloqueio de instância.</span><span class="sxs-lookup"><span data-stu-id="d44a4-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="d44a4-116">A operação não concluiu dentro do tempo limite distribuído de %1.</span><span class="sxs-lookup"><span data-stu-id="d44a4-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="d44a4-117">O tempo determinado para essa operação pode ter sido uma parte de um tempo limite maior.</span><span class="sxs-lookup"><span data-stu-id="d44a4-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d44a4-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d44a4-118">Details</span></span>  
  
|<span data-ttu-id="d44a4-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="d44a4-119">Data Item Name</span></span>|<span data-ttu-id="d44a4-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="d44a4-120">Data Item Type</span></span>|<span data-ttu-id="d44a4-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="d44a4-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d44a4-122">Atraso</span><span class="sxs-lookup"><span data-stu-id="d44a4-122">Delay</span></span>|<span data-ttu-id="d44a4-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="d44a4-123">xs:string</span></span>|<span data-ttu-id="d44a4-124">O atraso entre o tenta.</span><span class="sxs-lookup"><span data-stu-id="d44a4-124">The delay between retries.</span></span>|  
|<span data-ttu-id="d44a4-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d44a4-125">AppDomain</span></span>|<span data-ttu-id="d44a4-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="d44a4-126">xs:string</span></span>|<span data-ttu-id="d44a4-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d44a4-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
