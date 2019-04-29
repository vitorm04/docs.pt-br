---
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ede74eb642c5c2c79b90cf1458db424d9f83b087
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774238"
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="393d5-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="393d5-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="393d5-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="393d5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="393d5-104">ID</span><span class="sxs-lookup"><span data-stu-id="393d5-104">ID</span></span>|<span data-ttu-id="393d5-105">4211</span><span class="sxs-lookup"><span data-stu-id="393d5-105">4211</span></span>|  
|<span data-ttu-id="393d5-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="393d5-106">Keywords</span></span>|<span data-ttu-id="393d5-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="393d5-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="393d5-108">Nível</span><span class="sxs-lookup"><span data-stu-id="393d5-108">Level</span></span>|<span data-ttu-id="393d5-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="393d5-109">Warning</span></span>|  
|<span data-ttu-id="393d5-110">Canal</span><span class="sxs-lookup"><span data-stu-id="393d5-110">Channel</span></span>|<span data-ttu-id="393d5-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="393d5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="393d5-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="393d5-112">Description</span></span>  
 <span data-ttu-id="393d5-113">Indica a nova tentativa de enfileiramento SQL.</span><span class="sxs-lookup"><span data-stu-id="393d5-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="393d5-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="393d5-114">Message</span></span>  
 <span data-ttu-id="393d5-115">Nova tentativa SQL fila com atraso %1 milissegundos.</span><span class="sxs-lookup"><span data-stu-id="393d5-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="393d5-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="393d5-116">Details</span></span>  
  
|<span data-ttu-id="393d5-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="393d5-117">Data Item Name</span></span>|<span data-ttu-id="393d5-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="393d5-118">Data Item Type</span></span>|<span data-ttu-id="393d5-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="393d5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="393d5-120">Atraso</span><span class="sxs-lookup"><span data-stu-id="393d5-120">Delay</span></span>|<span data-ttu-id="393d5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="393d5-121">xs:string</span></span>|<span data-ttu-id="393d5-122">O atraso entre o tenta.</span><span class="sxs-lookup"><span data-stu-id="393d5-122">The delay between retries.</span></span>|  
|<span data-ttu-id="393d5-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="393d5-123">AppDomain</span></span>|<span data-ttu-id="393d5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="393d5-124">xs:string</span></span>|<span data-ttu-id="393d5-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="393d5-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
