---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eabc6a6915560d8c49e695d5d681f1544689cb07
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="92fe9-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="92fe9-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="92fe9-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="92fe9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="92fe9-104">ID</span><span class="sxs-lookup"><span data-stu-id="92fe9-104">ID</span></span>|<span data-ttu-id="92fe9-105">3550</span><span class="sxs-lookup"><span data-stu-id="92fe9-105">3550</span></span>|  
|<span data-ttu-id="92fe9-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="92fe9-106">Keywords</span></span>|<span data-ttu-id="92fe9-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="92fe9-107">WFServices</span></span>|  
|<span data-ttu-id="92fe9-108">Nível</span><span class="sxs-lookup"><span data-stu-id="92fe9-108">Level</span></span>|<span data-ttu-id="92fe9-109">Informações</span><span class="sxs-lookup"><span data-stu-id="92fe9-109">Information</span></span>|  
|<span data-ttu-id="92fe9-110">Canal</span><span class="sxs-lookup"><span data-stu-id="92fe9-110">Channel</span></span>|<span data-ttu-id="92fe9-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="92fe9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="92fe9-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="92fe9-112">Description</span></span>  
 <span data-ttu-id="92fe9-113">Indica que um armazenados em buffer recebe falhou.</span><span class="sxs-lookup"><span data-stu-id="92fe9-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="92fe9-114">A operação será tentada novamente quando a instância do serviço está pronta para processar esta operação específico.</span><span class="sxs-lookup"><span data-stu-id="92fe9-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="92fe9-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="92fe9-115">Message</span></span>  
 <span data-ttu-id="92fe9-116">A operação “%1 " não pode ser executada no momento.</span><span class="sxs-lookup"><span data-stu-id="92fe9-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="92fe9-117">Outra tentativa será feita quando a instância de serviço estiver pronta para processar esse operação específica.</span><span class="sxs-lookup"><span data-stu-id="92fe9-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="92fe9-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="92fe9-118">Details</span></span>  
  
|<span data-ttu-id="92fe9-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="92fe9-119">Data Item Name</span></span>|<span data-ttu-id="92fe9-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="92fe9-120">Data Item Type</span></span>|<span data-ttu-id="92fe9-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="92fe9-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="92fe9-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="92fe9-122">OperationName</span></span>|<span data-ttu-id="92fe9-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="92fe9-123">xs:string</span></span>|<span data-ttu-id="92fe9-124">O nome da operação.</span><span class="sxs-lookup"><span data-stu-id="92fe9-124">The name of the operation.</span></span>|  
|<span data-ttu-id="92fe9-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="92fe9-125">AppDomain</span></span>|<span data-ttu-id="92fe9-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="92fe9-126">xs:string</span></span>|<span data-ttu-id="92fe9-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="92fe9-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
