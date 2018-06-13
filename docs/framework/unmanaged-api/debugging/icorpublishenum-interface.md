---
title: Interface ICorPublishEnum
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3536184fa7798ac8eabe851221ec692c126460b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424008"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="5bb69-102">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="5bb69-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="5bb69-103">Serve como a interface base abstrata para os enumeradores que são usados na publicação de informações sobre domínios de aplicativos e processos.</span><span class="sxs-lookup"><span data-stu-id="5bb69-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5bb69-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5bb69-104">Methods</span></span>  
  
|<span data-ttu-id="5bb69-105">Método</span><span class="sxs-lookup"><span data-stu-id="5bb69-105">Method</span></span>|<span data-ttu-id="5bb69-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5bb69-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5bb69-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="5bb69-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="5bb69-108">Cria uma cópia deste objeto `ICorPublishEnum`.</span><span class="sxs-lookup"><span data-stu-id="5bb69-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="5bb69-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="5bb69-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="5bb69-110">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="5bb69-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="5bb69-111">Método Reset</span><span class="sxs-lookup"><span data-stu-id="5bb69-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="5bb69-112">Move o cursor de para o início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="5bb69-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="5bb69-113">Método Skip</span><span class="sxs-lookup"><span data-stu-id="5bb69-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="5bb69-114">Move o cursor para a frente na enumeração pelo número especificado de itens.</span><span class="sxs-lookup"><span data-stu-id="5bb69-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bb69-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="5bb69-115">Remarks</span></span>  
 <span data-ttu-id="5bb69-116">Os seguintes enumeradores derivam `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="5bb69-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
-   [<span data-ttu-id="5bb69-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="5bb69-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [<span data-ttu-id="5bb69-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="5bb69-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="5bb69-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5bb69-119">Requirements</span></span>  
 <span data-ttu-id="5bb69-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bb69-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bb69-121">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="5bb69-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="5bb69-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bb69-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bb69-123">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bb69-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bb69-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5bb69-124">See Also</span></span>  
 [<span data-ttu-id="5bb69-125">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="5bb69-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)  
 [<span data-ttu-id="5bb69-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5bb69-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
