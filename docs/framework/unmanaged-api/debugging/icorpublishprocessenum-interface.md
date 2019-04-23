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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173648"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="baf57-102">Interface ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="baf57-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="baf57-103">Uma subclasse do [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface que fornece métodos para percorrer uma coleção de [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="baf57-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="baf57-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="baf57-104">Methods</span></span>  
  
|<span data-ttu-id="baf57-105">Método</span><span class="sxs-lookup"><span data-stu-id="baf57-105">Method</span></span>|<span data-ttu-id="baf57-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="baf57-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="baf57-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="baf57-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="baf57-108">Obtém o número especificado de `ICorPublishProcess` instâncias da coleção, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="baf57-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baf57-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="baf57-109">Remarks</span></span>  
 <span data-ttu-id="baf57-110">O `ICorPublishProcessEnum` interface implementa os métodos da interface abstrata [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="baf57-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="baf57-111">Uma `ICorPublishProcessEnum` instância é criada pelo [icorpublish:: Enumprocesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="baf57-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="baf57-112">A passagem da coleção de `ICorPublishProcess` objetos é com base nos critérios de filtro fornecidos na ocasião do `ICorPublishProcessEnum` instância foi criada.</span><span class="sxs-lookup"><span data-stu-id="baf57-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baf57-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="baf57-113">Requirements</span></span>  
 <span data-ttu-id="baf57-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baf57-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baf57-115">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="baf57-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="baf57-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="baf57-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="baf57-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baf57-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf57-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="baf57-118">See also</span></span>

- [<span data-ttu-id="baf57-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="baf57-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="baf57-120">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="baf57-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
