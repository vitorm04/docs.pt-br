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
ms.workload: dotnet
ms.openlocfilehash: 435a6a4390d52555d353a25ac119934087cf9c87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="eb132-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="eb132-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="eb132-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="eb132-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eb132-104">ID</span><span class="sxs-lookup"><span data-stu-id="eb132-104">ID</span></span>|<span data-ttu-id="eb132-105">3550</span><span class="sxs-lookup"><span data-stu-id="eb132-105">3550</span></span>|  
|<span data-ttu-id="eb132-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="eb132-106">Keywords</span></span>|<span data-ttu-id="eb132-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="eb132-107">WFServices</span></span>|  
|<span data-ttu-id="eb132-108">Nível</span><span class="sxs-lookup"><span data-stu-id="eb132-108">Level</span></span>|<span data-ttu-id="eb132-109">Informações</span><span class="sxs-lookup"><span data-stu-id="eb132-109">Information</span></span>|  
|<span data-ttu-id="eb132-110">Canal</span><span class="sxs-lookup"><span data-stu-id="eb132-110">Channel</span></span>|<span data-ttu-id="eb132-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="eb132-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eb132-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb132-112">Description</span></span>  
 <span data-ttu-id="eb132-113">Indica que um armazenados em buffer recebe falhou.</span><span class="sxs-lookup"><span data-stu-id="eb132-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="eb132-114">A operação será tentada novamente quando a instância do serviço está pronta para processar esta operação específico.</span><span class="sxs-lookup"><span data-stu-id="eb132-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eb132-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="eb132-115">Message</span></span>  
 <span data-ttu-id="eb132-116">A operação “%1 " não pode ser executada no momento.</span><span class="sxs-lookup"><span data-stu-id="eb132-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="eb132-117">Outra tentativa será feita quando a instância de serviço estiver pronta para processar esse operação específica.</span><span class="sxs-lookup"><span data-stu-id="eb132-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="eb132-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="eb132-118">Details</span></span>  
  
|<span data-ttu-id="eb132-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="eb132-119">Data Item Name</span></span>|<span data-ttu-id="eb132-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="eb132-120">Data Item Type</span></span>|<span data-ttu-id="eb132-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb132-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eb132-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="eb132-122">OperationName</span></span>|<span data-ttu-id="eb132-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="eb132-123">xs:string</span></span>|<span data-ttu-id="eb132-124">O nome da operação.</span><span class="sxs-lookup"><span data-stu-id="eb132-124">The name of the operation.</span></span>|  
|<span data-ttu-id="eb132-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="eb132-125">AppDomain</span></span>|<span data-ttu-id="eb132-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="eb132-126">xs:string</span></span>|<span data-ttu-id="eb132-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="eb132-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
