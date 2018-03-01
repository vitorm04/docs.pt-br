---
title: Interface ICorPublishEnum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9f09d0f80eba86d03d0db7af8fd63d2231c9a88d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="b5dd8-102">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="b5dd8-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="b5dd8-103">Serve como a interface base abstrata para os enumeradores que são usados na publicação de informações sobre domínios de aplicativos e processos.</span><span class="sxs-lookup"><span data-stu-id="b5dd8-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b5dd8-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b5dd8-104">Methods</span></span>  
  
|<span data-ttu-id="b5dd8-105">Método</span><span class="sxs-lookup"><span data-stu-id="b5dd8-105">Method</span></span>|<span data-ttu-id="b5dd8-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5dd8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5dd8-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="b5dd8-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="b5dd8-108">Cria uma cópia deste objeto `ICorPublishEnum`.</span><span class="sxs-lookup"><span data-stu-id="b5dd8-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="b5dd8-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="b5dd8-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="b5dd8-110">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="b5dd8-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="b5dd8-111">Método Reset</span><span class="sxs-lookup"><span data-stu-id="b5dd8-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="b5dd8-112">Move o cursor de para o início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="b5dd8-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="b5dd8-113">Método Skip</span><span class="sxs-lookup"><span data-stu-id="b5dd8-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="b5dd8-114">Move o cursor para a frente na enumeração pelo número especificado de itens.</span><span class="sxs-lookup"><span data-stu-id="b5dd8-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5dd8-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="b5dd8-115">Remarks</span></span>  
 <span data-ttu-id="b5dd8-116">Os seguintes enumeradores derivam `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="b5dd8-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
-   [<span data-ttu-id="b5dd8-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="b5dd8-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [<span data-ttu-id="b5dd8-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="b5dd8-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="b5dd8-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5dd8-119">Requirements</span></span>  
 <span data-ttu-id="b5dd8-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5dd8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5dd8-121">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="b5dd8-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b5dd8-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5dd8-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5dd8-123">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5dd8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5dd8-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5dd8-124">See Also</span></span>  
 [<span data-ttu-id="b5dd8-125">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="b5dd8-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)  
 [<span data-ttu-id="b5dd8-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b5dd8-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
