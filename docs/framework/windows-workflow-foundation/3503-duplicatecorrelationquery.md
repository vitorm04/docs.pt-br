---
title: 3503 - DuplicateCorrelationQuery
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 997bdf4423364e9b5361635820849a6bde9e8960
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="a0017-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="a0017-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="a0017-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a0017-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a0017-104">ID</span><span class="sxs-lookup"><span data-stu-id="a0017-104">ID</span></span>|<span data-ttu-id="a0017-105">3503</span><span class="sxs-lookup"><span data-stu-id="a0017-105">3503</span></span>|  
|<span data-ttu-id="a0017-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="a0017-106">Keywords</span></span>|<span data-ttu-id="a0017-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="a0017-107">WFServices</span></span>|  
|<span data-ttu-id="a0017-108">Nível</span><span class="sxs-lookup"><span data-stu-id="a0017-108">Level</span></span>|<span data-ttu-id="a0017-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="a0017-109">Warning</span></span>|  
|<span data-ttu-id="a0017-110">Canal</span><span class="sxs-lookup"><span data-stu-id="a0017-110">Channel</span></span>|<span data-ttu-id="a0017-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="a0017-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a0017-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0017-112">Description</span></span>  
 <span data-ttu-id="a0017-113">Indica que um CorrelationQuery duplicado foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="a0017-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="a0017-114">A consulta duplicado não será usada para calcular correlação.</span><span class="sxs-lookup"><span data-stu-id="a0017-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a0017-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="a0017-115">Message</span></span>  
 <span data-ttu-id="a0017-116">Um CorrelationQuery duplicado foi encontrado com Where='%1.</span><span class="sxs-lookup"><span data-stu-id="a0017-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="a0017-117">Essa consulta duplicada não será usada no cálculo de correlação.</span><span class="sxs-lookup"><span data-stu-id="a0017-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a0017-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a0017-118">Details</span></span>  
  
|<span data-ttu-id="a0017-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="a0017-119">Data Item Name</span></span>|<span data-ttu-id="a0017-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="a0017-120">Data Item Type</span></span>|<span data-ttu-id="a0017-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0017-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a0017-122">Where</span><span class="sxs-lookup"><span data-stu-id="a0017-122">Where</span></span>|<span data-ttu-id="a0017-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="a0017-123">xs:string</span></span>|<span data-ttu-id="a0017-124">Onde parte da consulta de correlação.</span><span class="sxs-lookup"><span data-stu-id="a0017-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="a0017-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a0017-125">AppDomain</span></span>|<span data-ttu-id="a0017-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="a0017-126">xs:string</span></span>|<span data-ttu-id="a0017-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a0017-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
