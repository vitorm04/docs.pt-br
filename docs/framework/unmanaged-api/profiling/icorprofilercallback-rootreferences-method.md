---
title: Método ICorProfilerCallback::RootReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a68ea07c40c966422be6ebb663e62508032c2610
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750439"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="9089a-102">Método ICorProfilerCallback::RootReferences</span><span class="sxs-lookup"><span data-stu-id="9089a-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="9089a-103">Notifica o criador de perfil com informações sobre referências raiz após a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9089a-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9089a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9089a-104">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="9089a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9089a-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="9089a-106">[in] O número de referências no `rootRefIds` matriz.</span><span class="sxs-lookup"><span data-stu-id="9089a-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="9089a-107">[in] Uma matriz de IDs de objetos que fazem referência a um objeto estático ou um objeto na pilha.</span><span class="sxs-lookup"><span data-stu-id="9089a-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9089a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9089a-108">Remarks</span></span>  
 <span data-ttu-id="9089a-109">Ambos `RootReferences` e [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) são chamados para notificar o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="9089a-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="9089a-110">Os criadores de perfis normalmente implementará um ou outro, mas não ambos, porque as informações passadas `RootReferences2` é um superconjunto do que passado `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="9089a-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="9089a-111">É possível que o `rootRefIds` matriz para conter um objeto nulo.</span><span class="sxs-lookup"><span data-stu-id="9089a-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="9089a-112">Por exemplo, todas as referências de objeto declaradas na pilha são tratadas como raízes pelo coletor de lixo e sempre serão relatadas.</span><span class="sxs-lookup"><span data-stu-id="9089a-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="9089a-113">As IDs de objeto retornado por `RootReferences` não são válidos durante o retorno de chamada em si, porque a coleta de lixo pode estar no meio de mover objetos de endereços antigos para novos endereços.</span><span class="sxs-lookup"><span data-stu-id="9089a-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="9089a-114">Portanto, os criadores de perfis não devem tentar inspecionar objetos durante um `RootReferences` chamar.</span><span class="sxs-lookup"><span data-stu-id="9089a-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="9089a-115">Quando [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) é chamado, todos os objetos foram movidos para os novos locais e pode ser inspecionados com segurança.</span><span class="sxs-lookup"><span data-stu-id="9089a-115">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9089a-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9089a-116">Requirements</span></span>  
 <span data-ttu-id="9089a-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9089a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9089a-118">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9089a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9089a-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9089a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9089a-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9089a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9089a-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9089a-121">See also</span></span>

- [<span data-ttu-id="9089a-122">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="9089a-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
