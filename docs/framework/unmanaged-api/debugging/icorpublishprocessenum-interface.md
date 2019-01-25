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
ms.openlocfilehash: b72f2581b9670dbc110f2ab33cb861128bd78dca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525840"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="b53bf-102">Interface ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="b53bf-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="b53bf-103">Uma subclasse do [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface que fornece métodos para percorrer uma coleção de [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="b53bf-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b53bf-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b53bf-104">Methods</span></span>  
  
|<span data-ttu-id="b53bf-105">Método</span><span class="sxs-lookup"><span data-stu-id="b53bf-105">Method</span></span>|<span data-ttu-id="b53bf-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b53bf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b53bf-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="b53bf-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="b53bf-108">Obtém o número especificado de `ICorPublishProcess` instâncias da coleção, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="b53bf-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b53bf-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b53bf-109">Remarks</span></span>  
 <span data-ttu-id="b53bf-110">O `ICorPublishProcessEnum` interface implementa os métodos da interface abstrata [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b53bf-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="b53bf-111">Uma `ICorPublishProcessEnum` instância é criada pelo [icorpublish:: Enumprocesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b53bf-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="b53bf-112">A passagem da coleção de `ICorPublishProcess` objetos é com base nos critérios de filtro fornecidos na ocasião do `ICorPublishProcessEnum` instância foi criada.</span><span class="sxs-lookup"><span data-stu-id="b53bf-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b53bf-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b53bf-113">Requirements</span></span>  
 <span data-ttu-id="b53bf-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b53bf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b53bf-115">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="b53bf-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b53bf-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b53bf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b53bf-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b53bf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b53bf-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b53bf-118">See also</span></span>
- [<span data-ttu-id="b53bf-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b53bf-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b53bf-120">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="b53bf-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
