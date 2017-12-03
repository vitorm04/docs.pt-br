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
ms.openlocfilehash: 321d8c6185c8d24b7a3b6e255e235c36c119ff21
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="e4e09-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="e4e09-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="e4e09-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e4e09-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e4e09-104">ID</span><span class="sxs-lookup"><span data-stu-id="e4e09-104">ID</span></span>|<span data-ttu-id="e4e09-105">1132</span><span class="sxs-lookup"><span data-stu-id="e4e09-105">1132</span></span>|  
|<span data-ttu-id="e4e09-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="e4e09-106">Keywords</span></span>|<span data-ttu-id="e4e09-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e4e09-107">WFRuntime</span></span>|  
|<span data-ttu-id="e4e09-108">Nível</span><span class="sxs-lookup"><span data-stu-id="e4e09-108">Level</span></span>|<span data-ttu-id="e4e09-109">Informações</span><span class="sxs-lookup"><span data-stu-id="e4e09-109">Information</span></span>|  
|<span data-ttu-id="e4e09-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e4e09-110">Channel</span></span>|<span data-ttu-id="e4e09-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="e4e09-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e4e09-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4e09-112">Description</span></span>  
 <span data-ttu-id="e4e09-113">Durante a etapa de CacheMetadata, a atividade de InvokeMethod indica que não está usando o padrão de async ao chamar o método.</span><span class="sxs-lookup"><span data-stu-id="e4e09-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e4e09-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="e4e09-114">Message</span></span>  
 <span data-ttu-id="e4e09-115">InvokeMethod “%1" - o método não usa o padrão assíncrono.</span><span class="sxs-lookup"><span data-stu-id="e4e09-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e4e09-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e4e09-116">Details</span></span>  
  
|<span data-ttu-id="e4e09-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="e4e09-117">Data Item Name</span></span>|<span data-ttu-id="e4e09-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="e4e09-118">Data Item Type</span></span>|<span data-ttu-id="e4e09-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4e09-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e4e09-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="e4e09-120">InvokeMethod</span></span>|<span data-ttu-id="e4e09-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4e09-121">xs:string</span></span>|<span data-ttu-id="e4e09-122">O nome para exibição de atividade de InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="e4e09-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="e4e09-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e4e09-123">AppDomain</span></span>|<span data-ttu-id="e4e09-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4e09-124">xs:string</span></span>|<span data-ttu-id="e4e09-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e4e09-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
