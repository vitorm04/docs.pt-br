---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85e9456f6b4c1884b2e28671b304728135b6b1d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="2973c-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="2973c-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="2973c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2973c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2973c-104">ID</span><span class="sxs-lookup"><span data-stu-id="2973c-104">ID</span></span>|<span data-ttu-id="2973c-105">3557</span><span class="sxs-lookup"><span data-stu-id="2973c-105">3557</span></span>|  
|<span data-ttu-id="2973c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="2973c-106">Keywords</span></span>|<span data-ttu-id="2973c-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="2973c-107">WFServices</span></span>|  
|<span data-ttu-id="2973c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="2973c-108">Level</span></span>|<span data-ttu-id="2973c-109">Informações</span><span class="sxs-lookup"><span data-stu-id="2973c-109">Information</span></span>|  
|<span data-ttu-id="2973c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="2973c-110">Channel</span></span>|<span data-ttu-id="2973c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="2973c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2973c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2973c-112">Description</span></span>  
 <span data-ttu-id="2973c-113">Indica que a chamada a EndCommit em um CommittableTransaction apresentou um TransactionException.</span><span class="sxs-lookup"><span data-stu-id="2973c-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2973c-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="2973c-114">Message</span></span>  
 <span data-ttu-id="2973c-115">A chamada a EndCommit no CommittableTransaction com ID = “%1 " apresentou um TransactionException com a seguinte mensagem: “%2".</span><span class="sxs-lookup"><span data-stu-id="2973c-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2973c-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2973c-116">Details</span></span>  
  
|<span data-ttu-id="2973c-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="2973c-117">Data Item Name</span></span>|<span data-ttu-id="2973c-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="2973c-118">Data Item Type</span></span>|<span data-ttu-id="2973c-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="2973c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2973c-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="2973c-120">TransactionId</span></span>|<span data-ttu-id="2973c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="2973c-121">xs:string</span></span>|<span data-ttu-id="2973c-122">A identificação do CommittableTransaction.</span><span class="sxs-lookup"><span data-stu-id="2973c-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="2973c-123">Exceção</span><span class="sxs-lookup"><span data-stu-id="2973c-123">Exception</span></span>|<span data-ttu-id="2973c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="2973c-124">xs:string</span></span>|<span data-ttu-id="2973c-125">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="2973c-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="2973c-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2973c-126">AppDomain</span></span>|<span data-ttu-id="2973c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="2973c-127">xs:string</span></span>|<span data-ttu-id="2973c-128">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2973c-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
