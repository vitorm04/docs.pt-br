---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75386b56f7926b9ddb883e0ca212d795898fe6f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="176a1-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="176a1-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="176a1-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="176a1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="176a1-104">ID</span><span class="sxs-lookup"><span data-stu-id="176a1-104">ID</span></span>|<span data-ttu-id="176a1-105">1132</span><span class="sxs-lookup"><span data-stu-id="176a1-105">1132</span></span>|  
|<span data-ttu-id="176a1-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="176a1-106">Keywords</span></span>|<span data-ttu-id="176a1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="176a1-107">WFRuntime</span></span>|  
|<span data-ttu-id="176a1-108">Nível</span><span class="sxs-lookup"><span data-stu-id="176a1-108">Level</span></span>|<span data-ttu-id="176a1-109">Informações</span><span class="sxs-lookup"><span data-stu-id="176a1-109">Information</span></span>|  
|<span data-ttu-id="176a1-110">Canal</span><span class="sxs-lookup"><span data-stu-id="176a1-110">Channel</span></span>|<span data-ttu-id="176a1-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="176a1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="176a1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="176a1-112">Description</span></span>  
 <span data-ttu-id="176a1-113">Durante a etapa de CacheMetadata, a atividade de InvokeMethod indica que não está usando o padrão de async ao chamar o método.</span><span class="sxs-lookup"><span data-stu-id="176a1-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="176a1-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="176a1-114">Message</span></span>  
 <span data-ttu-id="176a1-115">InvokeMethod “%1" - o método não usa o padrão assíncrono.</span><span class="sxs-lookup"><span data-stu-id="176a1-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="176a1-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="176a1-116">Details</span></span>  
  
|<span data-ttu-id="176a1-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="176a1-117">Data Item Name</span></span>|<span data-ttu-id="176a1-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="176a1-118">Data Item Type</span></span>|<span data-ttu-id="176a1-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="176a1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="176a1-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="176a1-120">InvokeMethod</span></span>|<span data-ttu-id="176a1-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="176a1-121">xs:string</span></span>|<span data-ttu-id="176a1-122">O nome para exibição de atividade de InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="176a1-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="176a1-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="176a1-123">AppDomain</span></span>|<span data-ttu-id="176a1-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="176a1-124">xs:string</span></span>|<span data-ttu-id="176a1-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="176a1-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
