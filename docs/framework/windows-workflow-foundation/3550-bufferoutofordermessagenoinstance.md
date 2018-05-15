---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 1af943e23aa643c6614b946175c0b1854a7ceb62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="7528c-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="7528c-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="7528c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7528c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7528c-104">ID</span><span class="sxs-lookup"><span data-stu-id="7528c-104">ID</span></span>|<span data-ttu-id="7528c-105">3550</span><span class="sxs-lookup"><span data-stu-id="7528c-105">3550</span></span>|  
|<span data-ttu-id="7528c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="7528c-106">Keywords</span></span>|<span data-ttu-id="7528c-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="7528c-107">WFServices</span></span>|  
|<span data-ttu-id="7528c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="7528c-108">Level</span></span>|<span data-ttu-id="7528c-109">Informações</span><span class="sxs-lookup"><span data-stu-id="7528c-109">Information</span></span>|  
|<span data-ttu-id="7528c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="7528c-110">Channel</span></span>|<span data-ttu-id="7528c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="7528c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7528c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7528c-112">Description</span></span>  
 <span data-ttu-id="7528c-113">Indica que um armazenados em buffer recebe falhou.</span><span class="sxs-lookup"><span data-stu-id="7528c-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="7528c-114">A operação será tentada novamente quando a instância do serviço está pronta para processar esta operação específico.</span><span class="sxs-lookup"><span data-stu-id="7528c-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7528c-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="7528c-115">Message</span></span>  
 <span data-ttu-id="7528c-116">A operação “%1 " não pode ser executada no momento.</span><span class="sxs-lookup"><span data-stu-id="7528c-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="7528c-117">Outra tentativa será feita quando a instância de serviço estiver pronta para processar esse operação específica.</span><span class="sxs-lookup"><span data-stu-id="7528c-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7528c-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7528c-118">Details</span></span>  
  
|<span data-ttu-id="7528c-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="7528c-119">Data Item Name</span></span>|<span data-ttu-id="7528c-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="7528c-120">Data Item Type</span></span>|<span data-ttu-id="7528c-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="7528c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7528c-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="7528c-122">OperationName</span></span>|<span data-ttu-id="7528c-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="7528c-123">xs:string</span></span>|<span data-ttu-id="7528c-124">O nome da operação.</span><span class="sxs-lookup"><span data-stu-id="7528c-124">The name of the operation.</span></span>|  
|<span data-ttu-id="7528c-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7528c-125">AppDomain</span></span>|<span data-ttu-id="7528c-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="7528c-126">xs:string</span></span>|<span data-ttu-id="7528c-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7528c-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
