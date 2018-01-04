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
ms.workload: dotnet
ms.openlocfilehash: 1ffd44cf9d2333b22e3be809d05f2fa8c33d4cac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="3a392-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="3a392-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="3a392-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3a392-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a392-104">ID</span><span class="sxs-lookup"><span data-stu-id="3a392-104">ID</span></span>|<span data-ttu-id="3a392-105">4211</span><span class="sxs-lookup"><span data-stu-id="3a392-105">4211</span></span>|  
|<span data-ttu-id="3a392-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="3a392-106">Keywords</span></span>|<span data-ttu-id="3a392-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="3a392-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="3a392-108">Nível</span><span class="sxs-lookup"><span data-stu-id="3a392-108">Level</span></span>|<span data-ttu-id="3a392-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="3a392-109">Warning</span></span>|  
|<span data-ttu-id="3a392-110">Canal</span><span class="sxs-lookup"><span data-stu-id="3a392-110">Channel</span></span>|<span data-ttu-id="3a392-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="3a392-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3a392-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a392-112">Description</span></span>  
 <span data-ttu-id="3a392-113">Indica a nova tentativa de enfileiramento SQL.</span><span class="sxs-lookup"><span data-stu-id="3a392-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3a392-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="3a392-114">Message</span></span>  
 <span data-ttu-id="3a392-115">Nova tentativa SQL fila com atraso %1 milissegundos.</span><span class="sxs-lookup"><span data-stu-id="3a392-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3a392-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="3a392-116">Details</span></span>  
  
|<span data-ttu-id="3a392-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="3a392-117">Data Item Name</span></span>|<span data-ttu-id="3a392-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="3a392-118">Data Item Type</span></span>|<span data-ttu-id="3a392-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a392-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3a392-120">Atraso</span><span class="sxs-lookup"><span data-stu-id="3a392-120">Delay</span></span>|<span data-ttu-id="3a392-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3a392-121">xs:string</span></span>|<span data-ttu-id="3a392-122">O atraso entre o tenta.</span><span class="sxs-lookup"><span data-stu-id="3a392-122">The delay between retries.</span></span>|  
|<span data-ttu-id="3a392-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3a392-123">AppDomain</span></span>|<span data-ttu-id="3a392-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3a392-124">xs:string</span></span>|<span data-ttu-id="3a392-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3a392-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
