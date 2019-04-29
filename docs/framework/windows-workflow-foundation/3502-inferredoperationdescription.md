---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756085"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="01cae-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="01cae-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="01cae-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="01cae-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="01cae-104">ID</span><span class="sxs-lookup"><span data-stu-id="01cae-104">ID</span></span>|<span data-ttu-id="01cae-105">3502</span><span class="sxs-lookup"><span data-stu-id="01cae-105">3502</span></span>|  
|<span data-ttu-id="01cae-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="01cae-106">Keywords</span></span>|<span data-ttu-id="01cae-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="01cae-107">WFServices</span></span>|  
|<span data-ttu-id="01cae-108">Nível</span><span class="sxs-lookup"><span data-stu-id="01cae-108">Level</span></span>|<span data-ttu-id="01cae-109">Informações</span><span class="sxs-lookup"><span data-stu-id="01cae-109">Information</span></span>|  
|<span data-ttu-id="01cae-110">Canal</span><span class="sxs-lookup"><span data-stu-id="01cae-110">Channel</span></span>|<span data-ttu-id="01cae-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="01cae-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="01cae-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="01cae-112">Description</span></span>  
 <span data-ttu-id="01cae-113">Indica que um OperationDescription foi inferido de WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="01cae-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="01cae-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="01cae-114">Message</span></span>  
 <span data-ttu-id="01cae-115">OperationDescription com o Name='%1 no contrato “%2 " foi inferido de WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="01cae-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="01cae-116">IsOneWay=%3.</span><span class="sxs-lookup"><span data-stu-id="01cae-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="01cae-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="01cae-117">Details</span></span>  
  
|<span data-ttu-id="01cae-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="01cae-118">Data Item Name</span></span>|<span data-ttu-id="01cae-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="01cae-119">Data Item Type</span></span>|<span data-ttu-id="01cae-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="01cae-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="01cae-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="01cae-121">OperationName</span></span>|<span data-ttu-id="01cae-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="01cae-122">xs:string</span></span>|<span data-ttu-id="01cae-123">O nome da operação.</span><span class="sxs-lookup"><span data-stu-id="01cae-123">The name of the operation.</span></span>|  
|<span data-ttu-id="01cae-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="01cae-124">ContractName</span></span>|<span data-ttu-id="01cae-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="01cae-125">xs:string</span></span>|<span data-ttu-id="01cae-126">O nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="01cae-126">The name of the contract.</span></span>|  
|<span data-ttu-id="01cae-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="01cae-127">IsOneWay</span></span>|<span data-ttu-id="01cae-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="01cae-128">xs:string</span></span>|<span data-ttu-id="01cae-129">Retifique ou falso indicando se o contrato é unidirecional.</span><span class="sxs-lookup"><span data-stu-id="01cae-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="01cae-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="01cae-130">AppDomain</span></span>|<span data-ttu-id="01cae-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="01cae-131">xs:string</span></span>|<span data-ttu-id="01cae-132">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="01cae-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
