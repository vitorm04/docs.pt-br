---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511999"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="ef83c-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="ef83c-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="ef83c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ef83c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ef83c-104">ID</span><span class="sxs-lookup"><span data-stu-id="ef83c-104">ID</span></span>|<span data-ttu-id="ef83c-105">3502</span><span class="sxs-lookup"><span data-stu-id="ef83c-105">3502</span></span>|  
|<span data-ttu-id="ef83c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="ef83c-106">Keywords</span></span>|<span data-ttu-id="ef83c-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="ef83c-107">WFServices</span></span>|  
|<span data-ttu-id="ef83c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="ef83c-108">Level</span></span>|<span data-ttu-id="ef83c-109">Informações</span><span class="sxs-lookup"><span data-stu-id="ef83c-109">Information</span></span>|  
|<span data-ttu-id="ef83c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="ef83c-110">Channel</span></span>|<span data-ttu-id="ef83c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="ef83c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ef83c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef83c-112">Description</span></span>  
 <span data-ttu-id="ef83c-113">Indica que um OperationDescription foi inferido de WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="ef83c-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ef83c-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="ef83c-114">Message</span></span>  
 <span data-ttu-id="ef83c-115">OperationDescription com o Name='%1 no contrato “%2 " foi inferido de WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="ef83c-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="ef83c-116">IsOneWay=%3.</span><span class="sxs-lookup"><span data-stu-id="ef83c-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ef83c-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ef83c-117">Details</span></span>  
  
|<span data-ttu-id="ef83c-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="ef83c-118">Data Item Name</span></span>|<span data-ttu-id="ef83c-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="ef83c-119">Data Item Type</span></span>|<span data-ttu-id="ef83c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef83c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ef83c-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="ef83c-121">OperationName</span></span>|<span data-ttu-id="ef83c-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="ef83c-122">xs:string</span></span>|<span data-ttu-id="ef83c-123">O nome da operação.</span><span class="sxs-lookup"><span data-stu-id="ef83c-123">The name of the operation.</span></span>|  
|<span data-ttu-id="ef83c-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="ef83c-124">ContractName</span></span>|<span data-ttu-id="ef83c-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="ef83c-125">xs:string</span></span>|<span data-ttu-id="ef83c-126">O nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="ef83c-126">The name of the contract.</span></span>|  
|<span data-ttu-id="ef83c-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="ef83c-127">IsOneWay</span></span>|<span data-ttu-id="ef83c-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="ef83c-128">xs:string</span></span>|<span data-ttu-id="ef83c-129">Retifique ou falso indicando se o contrato é unidirecional.</span><span class="sxs-lookup"><span data-stu-id="ef83c-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="ef83c-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ef83c-130">AppDomain</span></span>|<span data-ttu-id="ef83c-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="ef83c-131">xs:string</span></span>|<span data-ttu-id="ef83c-132">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ef83c-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
