---
title: 1125 - InvokeMethodIsNotStatic
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b31bb8db8252474d20f7523e08cadf35bfcc84a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="b8b8f-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="b8b8f-102">1125 - InvokeMethodIsNotStatic</span></span>
## <a name="properties"></a><span data-ttu-id="b8b8f-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b8b8f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b8b8f-104">ID</span><span class="sxs-lookup"><span data-stu-id="b8b8f-104">ID</span></span>|<span data-ttu-id="b8b8f-105">1125</span><span class="sxs-lookup"><span data-stu-id="b8b8f-105">1125</span></span>|  
|<span data-ttu-id="b8b8f-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="b8b8f-106">Keywords</span></span>|<span data-ttu-id="b8b8f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b8b8f-107">WFRuntime</span></span>|  
|<span data-ttu-id="b8b8f-108">Nível</span><span class="sxs-lookup"><span data-stu-id="b8b8f-108">Level</span></span>|<span data-ttu-id="b8b8f-109">Informações</span><span class="sxs-lookup"><span data-stu-id="b8b8f-109">Information</span></span>|  
|<span data-ttu-id="b8b8f-110">Canal</span><span class="sxs-lookup"><span data-stu-id="b8b8f-110">Channel</span></span>|<span data-ttu-id="b8b8f-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="b8b8f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b8b8f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8b8f-112">Description</span></span>  
 <span data-ttu-id="b8b8f-113">Durante a etapa de CacheMetadata, a atividade de InvokeMethod indica que o método a ser chamado não é estático.</span><span class="sxs-lookup"><span data-stu-id="b8b8f-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b8b8f-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="b8b8f-114">Message</span></span>  
 <span data-ttu-id="b8b8f-115">InvokeMethod “%1" - o método não é estático.</span><span class="sxs-lookup"><span data-stu-id="b8b8f-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b8b8f-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="b8b8f-116">Details</span></span>  
  
|<span data-ttu-id="b8b8f-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="b8b8f-117">Data Item Name</span></span>|<span data-ttu-id="b8b8f-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="b8b8f-118">Data Item Type</span></span>|<span data-ttu-id="b8b8f-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8b8f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b8b8f-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="b8b8f-120">InvokeMethod</span></span>|<span data-ttu-id="b8b8f-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="b8b8f-121">xs:string</span></span>|<span data-ttu-id="b8b8f-122">O nome para exibição de atividade de InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="b8b8f-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="b8b8f-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b8b8f-123">AppDomain</span></span>|<span data-ttu-id="b8b8f-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="b8b8f-124">xs:string</span></span>|<span data-ttu-id="b8b8f-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b8b8f-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
