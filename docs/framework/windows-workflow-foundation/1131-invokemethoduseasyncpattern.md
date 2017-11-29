---
title: 1131 - InvokeMethodUseAsyncPattern
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6f9f8f4e836d5c5b437edcfaff6460c7b97210ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="5a1a2-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="5a1a2-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="5a1a2-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5a1a2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5a1a2-104">ID</span><span class="sxs-lookup"><span data-stu-id="5a1a2-104">ID</span></span>|<span data-ttu-id="5a1a2-105">1131</span><span class="sxs-lookup"><span data-stu-id="5a1a2-105">1131</span></span>|  
|<span data-ttu-id="5a1a2-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="5a1a2-106">Keywords</span></span>|<span data-ttu-id="5a1a2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5a1a2-107">WFRuntime</span></span>|  
|<span data-ttu-id="5a1a2-108">Nível</span><span class="sxs-lookup"><span data-stu-id="5a1a2-108">Level</span></span>|<span data-ttu-id="5a1a2-109">Informações</span><span class="sxs-lookup"><span data-stu-id="5a1a2-109">Information</span></span>|  
|<span data-ttu-id="5a1a2-110">Canal</span><span class="sxs-lookup"><span data-stu-id="5a1a2-110">Channel</span></span>|<span data-ttu-id="5a1a2-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="5a1a2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5a1a2-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a1a2-112">Description</span></span>  
 <span data-ttu-id="5a1a2-113">Durante a etapa de CacheMetadata, a atividade de InvokeMethod indica que está usando o padrão de async ao chamar o método.</span><span class="sxs-lookup"><span data-stu-id="5a1a2-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5a1a2-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="5a1a2-114">Message</span></span>  
 <span data-ttu-id="5a1a2-115">InvokeMethod “%1 " - o método utiliza o padrão assíncrono de “%2 " e “%3 ".</span><span class="sxs-lookup"><span data-stu-id="5a1a2-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5a1a2-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5a1a2-116">Details</span></span>  
  
|<span data-ttu-id="5a1a2-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="5a1a2-117">Data Item Name</span></span>|<span data-ttu-id="5a1a2-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="5a1a2-118">Data Item Type</span></span>|<span data-ttu-id="5a1a2-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a1a2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5a1a2-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="5a1a2-120">InvokeMethod</span></span>|<span data-ttu-id="5a1a2-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="5a1a2-121">xs:string</span></span>|<span data-ttu-id="5a1a2-122">O nome para exibição de atividade de InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="5a1a2-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="5a1a2-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="5a1a2-123">BeginMethod</span></span>|<span data-ttu-id="5a1a2-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="5a1a2-124">xs:string</span></span>|<span data-ttu-id="5a1a2-125">O nome do método inicial.</span><span class="sxs-lookup"><span data-stu-id="5a1a2-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="5a1a2-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="5a1a2-126">EndMethod</span></span>|<span data-ttu-id="5a1a2-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="5a1a2-127">xs:string</span></span>|<span data-ttu-id="5a1a2-128">O nome do método final.</span><span class="sxs-lookup"><span data-stu-id="5a1a2-128">The name of the end method.</span></span>|  
|<span data-ttu-id="5a1a2-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5a1a2-129">AppDomain</span></span>|<span data-ttu-id="5a1a2-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="5a1a2-130">xs:string</span></span>|<span data-ttu-id="5a1a2-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5a1a2-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
