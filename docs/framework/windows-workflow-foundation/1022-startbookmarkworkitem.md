---
title: 1022 - StartBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9aaabbdca455d31d22b232ae2b08edef0687ac30
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="13bf2-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="13bf2-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="13bf2-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="13bf2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="13bf2-104">ID</span><span class="sxs-lookup"><span data-stu-id="13bf2-104">ID</span></span>|<span data-ttu-id="13bf2-105">1022</span><span class="sxs-lookup"><span data-stu-id="13bf2-105">1022</span></span>|  
|<span data-ttu-id="13bf2-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="13bf2-106">Keywords</span></span>|<span data-ttu-id="13bf2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="13bf2-107">WFRuntime</span></span>|  
|<span data-ttu-id="13bf2-108">Nível</span><span class="sxs-lookup"><span data-stu-id="13bf2-108">Level</span></span>|<span data-ttu-id="13bf2-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="13bf2-109">Verbose</span></span>|  
|<span data-ttu-id="13bf2-110">Canal</span><span class="sxs-lookup"><span data-stu-id="13bf2-110">Channel</span></span>|<span data-ttu-id="13bf2-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="13bf2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="13bf2-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="13bf2-112">Description</span></span>  
 <span data-ttu-id="13bf2-113">Indica que um BookmarkWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="13bf2-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="13bf2-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="13bf2-114">Message</span></span>  
 <span data-ttu-id="13bf2-115">Iniciando a execução de um BookmarkWorkItem para a atividade '%1', DisplayName: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="13bf2-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="13bf2-116">BookmarkName: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="13bf2-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="13bf2-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="13bf2-117">Details</span></span>  
  
|<span data-ttu-id="13bf2-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="13bf2-118">Data Item Name</span></span>|<span data-ttu-id="13bf2-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="13bf2-119">Data Item Type</span></span>|<span data-ttu-id="13bf2-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="13bf2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="13bf2-121">Atividade</span><span class="sxs-lookup"><span data-stu-id="13bf2-121">Activity</span></span>|<span data-ttu-id="13bf2-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="13bf2-122">xs:string</span></span>|<span data-ttu-id="13bf2-123">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="13bf2-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="13bf2-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="13bf2-124">DisplayName</span></span>|<span data-ttu-id="13bf2-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="13bf2-125">xs:string</span></span>|<span data-ttu-id="13bf2-126">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="13bf2-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="13bf2-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="13bf2-127">InstanceId</span></span>|<span data-ttu-id="13bf2-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="13bf2-128">xs:string</span></span>|<span data-ttu-id="13bf2-129">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="13bf2-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="13bf2-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="13bf2-130">BookmarkName</span></span>|<span data-ttu-id="13bf2-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="13bf2-131">xs:string</span></span>|<span data-ttu-id="13bf2-132">O nome do indicador.</span><span class="sxs-lookup"><span data-stu-id="13bf2-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="13bf2-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="13bf2-133">BookmarkScope</span></span>|<span data-ttu-id="13bf2-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="13bf2-134">xs:string</span></span>|<span data-ttu-id="13bf2-135">O escopo do indexador.</span><span class="sxs-lookup"><span data-stu-id="13bf2-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="13bf2-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="13bf2-136">AppDomain</span></span>|<span data-ttu-id="13bf2-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="13bf2-137">xs:string</span></span>|<span data-ttu-id="13bf2-138">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="13bf2-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
