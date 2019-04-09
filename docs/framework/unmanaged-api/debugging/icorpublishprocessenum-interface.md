---
title: Interface ICorPublishProcessEnum
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5186df61eb82b29fcfa9776408498b748068e122
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173648"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="59894-102">Interface ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="59894-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="59894-103">Uma subclasse do [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface que fornece métodos para percorrer uma coleção de [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="59894-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59894-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="59894-104">Methods</span></span>  
  
|<span data-ttu-id="59894-105">Método</span><span class="sxs-lookup"><span data-stu-id="59894-105">Method</span></span>|<span data-ttu-id="59894-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="59894-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59894-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="59894-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="59894-108">Obtém o número especificado de `ICorPublishProcess` instâncias da coleção, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="59894-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59894-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="59894-109">Remarks</span></span>  
 <span data-ttu-id="59894-110">O `ICorPublishProcessEnum` interface implementa os métodos da interface abstrata [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="59894-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="59894-111">Uma `ICorPublishProcessEnum` instância é criada pelo [icorpublish:: Enumprocesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="59894-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="59894-112">A passagem da coleção de `ICorPublishProcess` objetos é com base nos critérios de filtro fornecidos na ocasião do `ICorPublishProcessEnum` instância foi criada.</span><span class="sxs-lookup"><span data-stu-id="59894-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59894-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="59894-113">Requirements</span></span>  
 <span data-ttu-id="59894-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59894-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59894-115">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="59894-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="59894-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59894-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="59894-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="59894-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="59894-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59894-118">See also</span></span>

- [<span data-ttu-id="59894-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="59894-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="59894-120">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="59894-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
