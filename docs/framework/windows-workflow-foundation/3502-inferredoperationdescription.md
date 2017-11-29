---
title: 3502 - InferredOperationDescription
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 044d67bc2b721451ade04947484899266d288d8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="e162c-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="e162c-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="e162c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e162c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e162c-104">ID</span><span class="sxs-lookup"><span data-stu-id="e162c-104">ID</span></span>|<span data-ttu-id="e162c-105">3502</span><span class="sxs-lookup"><span data-stu-id="e162c-105">3502</span></span>|  
|<span data-ttu-id="e162c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="e162c-106">Keywords</span></span>|<span data-ttu-id="e162c-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="e162c-107">WFServices</span></span>|  
|<span data-ttu-id="e162c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="e162c-108">Level</span></span>|<span data-ttu-id="e162c-109">Informações</span><span class="sxs-lookup"><span data-stu-id="e162c-109">Information</span></span>|  
|<span data-ttu-id="e162c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e162c-110">Channel</span></span>|<span data-ttu-id="e162c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="e162c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e162c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e162c-112">Description</span></span>  
 <span data-ttu-id="e162c-113">Indica que um OperationDescription foi inferido de WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="e162c-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e162c-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="e162c-114">Message</span></span>  
 <span data-ttu-id="e162c-115">OperationDescription com o Name='%1 no contrato “%2 " foi inferido de WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="e162c-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="e162c-116">IsOneWay=%3.</span><span class="sxs-lookup"><span data-stu-id="e162c-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e162c-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e162c-117">Details</span></span>  
  
|<span data-ttu-id="e162c-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="e162c-118">Data Item Name</span></span>|<span data-ttu-id="e162c-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="e162c-119">Data Item Type</span></span>|<span data-ttu-id="e162c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="e162c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e162c-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="e162c-121">OperationName</span></span>|<span data-ttu-id="e162c-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e162c-122">xs:string</span></span>|<span data-ttu-id="e162c-123">O nome da operação.</span><span class="sxs-lookup"><span data-stu-id="e162c-123">The name of the operation.</span></span>|  
|<span data-ttu-id="e162c-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="e162c-124">ContractName</span></span>|<span data-ttu-id="e162c-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e162c-125">xs:string</span></span>|<span data-ttu-id="e162c-126">O nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="e162c-126">The name of the contract.</span></span>|  
|<span data-ttu-id="e162c-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="e162c-127">IsOneWay</span></span>|<span data-ttu-id="e162c-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="e162c-128">xs:string</span></span>|<span data-ttu-id="e162c-129">Retifique ou falso indicando se o contrato é unidirecional.</span><span class="sxs-lookup"><span data-stu-id="e162c-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="e162c-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e162c-130">AppDomain</span></span>|<span data-ttu-id="e162c-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="e162c-131">xs:string</span></span>|<span data-ttu-id="e162c-132">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e162c-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
