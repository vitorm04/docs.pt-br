---
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ede74eb642c5c2c79b90cf1458db424d9f83b087
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514563"
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="3a0b7-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="3a0b7-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="3a0b7-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3a0b7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a0b7-104">ID</span><span class="sxs-lookup"><span data-stu-id="3a0b7-104">ID</span></span>|<span data-ttu-id="3a0b7-105">4211</span><span class="sxs-lookup"><span data-stu-id="3a0b7-105">4211</span></span>|  
|<span data-ttu-id="3a0b7-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="3a0b7-106">Keywords</span></span>|<span data-ttu-id="3a0b7-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="3a0b7-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="3a0b7-108">Nível</span><span class="sxs-lookup"><span data-stu-id="3a0b7-108">Level</span></span>|<span data-ttu-id="3a0b7-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="3a0b7-109">Warning</span></span>|  
|<span data-ttu-id="3a0b7-110">Canal</span><span class="sxs-lookup"><span data-stu-id="3a0b7-110">Channel</span></span>|<span data-ttu-id="3a0b7-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="3a0b7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3a0b7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a0b7-112">Description</span></span>  
 <span data-ttu-id="3a0b7-113">Indica a nova tentativa de enfileiramento SQL.</span><span class="sxs-lookup"><span data-stu-id="3a0b7-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3a0b7-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="3a0b7-114">Message</span></span>  
 <span data-ttu-id="3a0b7-115">Nova tentativa SQL fila com atraso %1 milissegundos.</span><span class="sxs-lookup"><span data-stu-id="3a0b7-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3a0b7-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="3a0b7-116">Details</span></span>  
  
|<span data-ttu-id="3a0b7-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="3a0b7-117">Data Item Name</span></span>|<span data-ttu-id="3a0b7-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="3a0b7-118">Data Item Type</span></span>|<span data-ttu-id="3a0b7-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a0b7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3a0b7-120">Atraso</span><span class="sxs-lookup"><span data-stu-id="3a0b7-120">Delay</span></span>|<span data-ttu-id="3a0b7-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3a0b7-121">xs:string</span></span>|<span data-ttu-id="3a0b7-122">O atraso entre o tenta.</span><span class="sxs-lookup"><span data-stu-id="3a0b7-122">The delay between retries.</span></span>|  
|<span data-ttu-id="3a0b7-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3a0b7-123">AppDomain</span></span>|<span data-ttu-id="3a0b7-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3a0b7-124">xs:string</span></span>|<span data-ttu-id="3a0b7-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3a0b7-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
