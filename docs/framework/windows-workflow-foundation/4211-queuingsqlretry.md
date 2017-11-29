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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c318ee6509ce8b96a1e7e78a13f4aeb7c76dde6a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="41af4-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="41af4-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="41af4-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="41af4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="41af4-104">ID</span><span class="sxs-lookup"><span data-stu-id="41af4-104">ID</span></span>|<span data-ttu-id="41af4-105">4211</span><span class="sxs-lookup"><span data-stu-id="41af4-105">4211</span></span>|  
|<span data-ttu-id="41af4-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="41af4-106">Keywords</span></span>|<span data-ttu-id="41af4-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="41af4-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="41af4-108">Nível</span><span class="sxs-lookup"><span data-stu-id="41af4-108">Level</span></span>|<span data-ttu-id="41af4-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="41af4-109">Warning</span></span>|  
|<span data-ttu-id="41af4-110">Canal</span><span class="sxs-lookup"><span data-stu-id="41af4-110">Channel</span></span>|<span data-ttu-id="41af4-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="41af4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="41af4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="41af4-112">Description</span></span>  
 <span data-ttu-id="41af4-113">Indica a nova tentativa de enfileiramento SQL.</span><span class="sxs-lookup"><span data-stu-id="41af4-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="41af4-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="41af4-114">Message</span></span>  
 <span data-ttu-id="41af4-115">Nova tentativa SQL fila com atraso %1 milissegundos.</span><span class="sxs-lookup"><span data-stu-id="41af4-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="41af4-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="41af4-116">Details</span></span>  
  
|<span data-ttu-id="41af4-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="41af4-117">Data Item Name</span></span>|<span data-ttu-id="41af4-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="41af4-118">Data Item Type</span></span>|<span data-ttu-id="41af4-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="41af4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="41af4-120">Atraso</span><span class="sxs-lookup"><span data-stu-id="41af4-120">Delay</span></span>|<span data-ttu-id="41af4-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="41af4-121">xs:string</span></span>|<span data-ttu-id="41af4-122">O atraso entre o tenta.</span><span class="sxs-lookup"><span data-stu-id="41af4-122">The delay between retries.</span></span>|  
|<span data-ttu-id="41af4-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="41af4-123">AppDomain</span></span>|<span data-ttu-id="41af4-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="41af4-124">xs:string</span></span>|<span data-ttu-id="41af4-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="41af4-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
