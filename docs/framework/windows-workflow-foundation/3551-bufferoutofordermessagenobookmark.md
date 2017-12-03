---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6dc505a4e0e79b37f9adff41b80dcba55215576f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="ad9c6-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="ad9c6-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="ad9c6-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ad9c6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad9c6-104">ID</span><span class="sxs-lookup"><span data-stu-id="ad9c6-104">ID</span></span>|<span data-ttu-id="ad9c6-105">3551</span><span class="sxs-lookup"><span data-stu-id="ad9c6-105">3551</span></span>|  
|<span data-ttu-id="ad9c6-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="ad9c6-106">Keywords</span></span>|<span data-ttu-id="ad9c6-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="ad9c6-107">WFServices</span></span>|  
|<span data-ttu-id="ad9c6-108">Nível</span><span class="sxs-lookup"><span data-stu-id="ad9c6-108">Level</span></span>|<span data-ttu-id="ad9c6-109">Informações</span><span class="sxs-lookup"><span data-stu-id="ad9c6-109">Information</span></span>|  
|<span data-ttu-id="ad9c6-110">Canal</span><span class="sxs-lookup"><span data-stu-id="ad9c6-110">Channel</span></span>|<span data-ttu-id="ad9c6-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="ad9c6-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ad9c6-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad9c6-112">Description</span></span>  
 <span data-ttu-id="ad9c6-113">Indica que uma ressunção do indexador falhou.</span><span class="sxs-lookup"><span data-stu-id="ad9c6-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="ad9c6-114">O armazenados em buffer recebe a operação será tentada novamente quando a instância do serviço está pronta para processar esta operação específico.</span><span class="sxs-lookup"><span data-stu-id="ad9c6-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ad9c6-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="ad9c6-115">Message</span></span>  
 <span data-ttu-id="ad9c6-116">A operação “%2 " na instância “%1 " do serviço não pode ser executada no momento.</span><span class="sxs-lookup"><span data-stu-id="ad9c6-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="ad9c6-117">Outra tentativa será feita quando a instância de serviço estiver pronta para processar esse operação específica.</span><span class="sxs-lookup"><span data-stu-id="ad9c6-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ad9c6-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ad9c6-118">Details</span></span>  
  
|<span data-ttu-id="ad9c6-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="ad9c6-119">Data Item Name</span></span>|<span data-ttu-id="ad9c6-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="ad9c6-120">Data Item Type</span></span>|<span data-ttu-id="ad9c6-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad9c6-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ad9c6-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="ad9c6-122">OperationName</span></span>|<span data-ttu-id="ad9c6-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="ad9c6-123">xs:string</span></span>|<span data-ttu-id="ad9c6-124">O nome da operação.</span><span class="sxs-lookup"><span data-stu-id="ad9c6-124">The name of the operation.</span></span>|  
|<span data-ttu-id="ad9c6-125">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="ad9c6-125">ServiceInstanceId</span></span>|<span data-ttu-id="ad9c6-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="ad9c6-126">xs:string</span></span>|<span data-ttu-id="ad9c6-127">A identificação da instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="ad9c6-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="ad9c6-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ad9c6-128">AppDomain</span></span>|<span data-ttu-id="ad9c6-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="ad9c6-129">xs:string</span></span>|<span data-ttu-id="ad9c6-130">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ad9c6-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
