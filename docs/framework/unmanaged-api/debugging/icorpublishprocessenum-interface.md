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
ms.openlocfilehash: 3a7267548a957d403cfe02aa3d800a410c14b82a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103424"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="8a2b0-102">Interface ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="8a2b0-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="8a2b0-103">Uma subclasse da interface [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) que fornece métodos para atravessar uma coleção de objetos [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8a2b0-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a2b0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="8a2b0-104">Methods</span></span>  
  
|<span data-ttu-id="8a2b0-105">Método</span><span class="sxs-lookup"><span data-stu-id="8a2b0-105">Method</span></span>|<span data-ttu-id="8a2b0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a2b0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a2b0-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="8a2b0-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="8a2b0-108">Obtém o número especificado de instâncias de `ICorPublishProcess` da coleção, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="8a2b0-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a2b0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a2b0-109">Remarks</span></span>  
 <span data-ttu-id="8a2b0-110">A interface `ICorPublishProcessEnum` implementa os métodos da interface abstrata, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8a2b0-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="8a2b0-111">Uma instância de `ICorPublishProcessEnum` é criada pelo método [ICorPublish:: EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8a2b0-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="8a2b0-112">A passagem da coleção de objetos de `ICorPublishProcess` é baseada nos critérios de filtro fornecidos no momento em que a instância de `ICorPublishProcessEnum` foi criada.</span><span class="sxs-lookup"><span data-stu-id="8a2b0-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a2b0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a2b0-113">Requirements</span></span>  
 <span data-ttu-id="8a2b0-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a2b0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a2b0-115">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="8a2b0-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="8a2b0-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a2b0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a2b0-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a2b0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a2b0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a2b0-118">See also</span></span>

- [<span data-ttu-id="8a2b0-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8a2b0-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8a2b0-120">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="8a2b0-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
