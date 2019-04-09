---
title: Interface ICorPublishAppDomainEnum
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f6d4af7c01f91dff77d6ba715ef845f523c7fb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090015"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="b91e2-102">Interface ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="b91e2-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="b91e2-103">Uma subclasse do [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface que fornece métodos para percorrer uma coleção de [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objetos que existem atualmente dentro de um processo.</span><span class="sxs-lookup"><span data-stu-id="b91e2-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b91e2-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b91e2-104">Methods</span></span>  
  
|<span data-ttu-id="b91e2-105">Método</span><span class="sxs-lookup"><span data-stu-id="b91e2-105">Method</span></span>|<span data-ttu-id="b91e2-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b91e2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b91e2-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="b91e2-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="b91e2-108">Obtém o número especificado de `ICorPublishAppDomain` instâncias da coleção, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="b91e2-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b91e2-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b91e2-109">Remarks</span></span>  
 <span data-ttu-id="b91e2-110">O `ICorPublishAppDomainEnum` interface implementa os métodos da interface abstrata [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b91e2-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b91e2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b91e2-111">Requirements</span></span>  
 <span data-ttu-id="b91e2-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b91e2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b91e2-113">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="b91e2-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b91e2-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b91e2-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b91e2-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b91e2-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b91e2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b91e2-116">See also</span></span>

- [<span data-ttu-id="b91e2-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b91e2-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b91e2-118">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="b91e2-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
