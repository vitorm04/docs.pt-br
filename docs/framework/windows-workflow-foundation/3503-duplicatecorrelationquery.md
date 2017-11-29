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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 60367b33e1e57cce8646b4fcde79c7d4fd20a4cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="bcda5-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="bcda5-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="bcda5-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="bcda5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bcda5-104">ID</span><span class="sxs-lookup"><span data-stu-id="bcda5-104">ID</span></span>|<span data-ttu-id="bcda5-105">3503</span><span class="sxs-lookup"><span data-stu-id="bcda5-105">3503</span></span>|  
|<span data-ttu-id="bcda5-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="bcda5-106">Keywords</span></span>|<span data-ttu-id="bcda5-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="bcda5-107">WFServices</span></span>|  
|<span data-ttu-id="bcda5-108">Nível</span><span class="sxs-lookup"><span data-stu-id="bcda5-108">Level</span></span>|<span data-ttu-id="bcda5-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="bcda5-109">Warning</span></span>|  
|<span data-ttu-id="bcda5-110">Canal</span><span class="sxs-lookup"><span data-stu-id="bcda5-110">Channel</span></span>|<span data-ttu-id="bcda5-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="bcda5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bcda5-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="bcda5-112">Description</span></span>  
 <span data-ttu-id="bcda5-113">Indica que um CorrelationQuery duplicado foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="bcda5-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="bcda5-114">A consulta duplicado não será usada para calcular correlação.</span><span class="sxs-lookup"><span data-stu-id="bcda5-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bcda5-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="bcda5-115">Message</span></span>  
 <span data-ttu-id="bcda5-116">Um CorrelationQuery duplicado foi encontrado com Where='%1.</span><span class="sxs-lookup"><span data-stu-id="bcda5-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="bcda5-117">Essa consulta duplicada não será usada no cálculo de correlação.</span><span class="sxs-lookup"><span data-stu-id="bcda5-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bcda5-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="bcda5-118">Details</span></span>  
  
|<span data-ttu-id="bcda5-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="bcda5-119">Data Item Name</span></span>|<span data-ttu-id="bcda5-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="bcda5-120">Data Item Type</span></span>|<span data-ttu-id="bcda5-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="bcda5-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bcda5-122">Where</span><span class="sxs-lookup"><span data-stu-id="bcda5-122">Where</span></span>|<span data-ttu-id="bcda5-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="bcda5-123">xs:string</span></span>|<span data-ttu-id="bcda5-124">Onde parte da consulta de correlação.</span><span class="sxs-lookup"><span data-stu-id="bcda5-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="bcda5-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bcda5-125">AppDomain</span></span>|<span data-ttu-id="bcda5-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="bcda5-126">xs:string</span></span>|<span data-ttu-id="bcda5-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="bcda5-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
