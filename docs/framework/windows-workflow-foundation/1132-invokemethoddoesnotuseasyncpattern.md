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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 300e843529bfc76df4193b46cd713ce0bd9cdbfd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="f6a46-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="f6a46-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="f6a46-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f6a46-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f6a46-104">ID</span><span class="sxs-lookup"><span data-stu-id="f6a46-104">ID</span></span>|<span data-ttu-id="f6a46-105">1132</span><span class="sxs-lookup"><span data-stu-id="f6a46-105">1132</span></span>|  
|<span data-ttu-id="f6a46-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="f6a46-106">Keywords</span></span>|<span data-ttu-id="f6a46-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f6a46-107">WFRuntime</span></span>|  
|<span data-ttu-id="f6a46-108">Nível</span><span class="sxs-lookup"><span data-stu-id="f6a46-108">Level</span></span>|<span data-ttu-id="f6a46-109">Informações</span><span class="sxs-lookup"><span data-stu-id="f6a46-109">Information</span></span>|  
|<span data-ttu-id="f6a46-110">Canal</span><span class="sxs-lookup"><span data-stu-id="f6a46-110">Channel</span></span>|<span data-ttu-id="f6a46-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="f6a46-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f6a46-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6a46-112">Description</span></span>  
 <span data-ttu-id="f6a46-113">Durante a etapa de CacheMetadata, a atividade de InvokeMethod indica que não está usando o padrão de async ao chamar o método.</span><span class="sxs-lookup"><span data-stu-id="f6a46-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f6a46-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="f6a46-114">Message</span></span>  
 <span data-ttu-id="f6a46-115">InvokeMethod “%1" - o método não usa o padrão assíncrono.</span><span class="sxs-lookup"><span data-stu-id="f6a46-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f6a46-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f6a46-116">Details</span></span>  
  
|<span data-ttu-id="f6a46-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="f6a46-117">Data Item Name</span></span>|<span data-ttu-id="f6a46-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="f6a46-118">Data Item Type</span></span>|<span data-ttu-id="f6a46-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6a46-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f6a46-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="f6a46-120">InvokeMethod</span></span>|<span data-ttu-id="f6a46-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6a46-121">xs:string</span></span>|<span data-ttu-id="f6a46-122">O nome para exibição de atividade de InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="f6a46-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="f6a46-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f6a46-123">AppDomain</span></span>|<span data-ttu-id="f6a46-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6a46-124">xs:string</span></span>|<span data-ttu-id="f6a46-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f6a46-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
