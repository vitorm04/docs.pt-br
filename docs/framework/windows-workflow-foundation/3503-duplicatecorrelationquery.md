---
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: 37a689b30b0bcab9124472deb98627afbe30dfee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511394"
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="ccda4-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="ccda4-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="ccda4-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ccda4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ccda4-104">ID</span><span class="sxs-lookup"><span data-stu-id="ccda4-104">ID</span></span>|<span data-ttu-id="ccda4-105">3503</span><span class="sxs-lookup"><span data-stu-id="ccda4-105">3503</span></span>|  
|<span data-ttu-id="ccda4-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="ccda4-106">Keywords</span></span>|<span data-ttu-id="ccda4-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="ccda4-107">WFServices</span></span>|  
|<span data-ttu-id="ccda4-108">Nível</span><span class="sxs-lookup"><span data-stu-id="ccda4-108">Level</span></span>|<span data-ttu-id="ccda4-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="ccda4-109">Warning</span></span>|  
|<span data-ttu-id="ccda4-110">Canal</span><span class="sxs-lookup"><span data-stu-id="ccda4-110">Channel</span></span>|<span data-ttu-id="ccda4-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="ccda4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ccda4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccda4-112">Description</span></span>  
 <span data-ttu-id="ccda4-113">Indica que um CorrelationQuery duplicado foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="ccda4-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="ccda4-114">A consulta duplicado não será usada para calcular correlação.</span><span class="sxs-lookup"><span data-stu-id="ccda4-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ccda4-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="ccda4-115">Message</span></span>  
 <span data-ttu-id="ccda4-116">Um CorrelationQuery duplicado foi encontrado com Where='%1.</span><span class="sxs-lookup"><span data-stu-id="ccda4-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="ccda4-117">Essa consulta duplicada não será usada no cálculo de correlação.</span><span class="sxs-lookup"><span data-stu-id="ccda4-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ccda4-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ccda4-118">Details</span></span>  
  
|<span data-ttu-id="ccda4-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="ccda4-119">Data Item Name</span></span>|<span data-ttu-id="ccda4-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="ccda4-120">Data Item Type</span></span>|<span data-ttu-id="ccda4-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccda4-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ccda4-122">Where</span><span class="sxs-lookup"><span data-stu-id="ccda4-122">Where</span></span>|<span data-ttu-id="ccda4-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="ccda4-123">xs:string</span></span>|<span data-ttu-id="ccda4-124">Onde parte da consulta de correlação.</span><span class="sxs-lookup"><span data-stu-id="ccda4-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="ccda4-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ccda4-125">AppDomain</span></span>|<span data-ttu-id="ccda4-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="ccda4-126">xs:string</span></span>|<span data-ttu-id="ccda4-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ccda4-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
