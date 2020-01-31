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
ms.openlocfilehash: 948628f469eecabfbbe792dcc3edf2e1204ffc36
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865955"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="21e79-102">Método ICorProfilerCallback::RootReferences</span><span class="sxs-lookup"><span data-stu-id="21e79-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="21e79-103">Notifica o criador de perfil com informações sobre referências raiz após a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="21e79-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e79-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21e79-104">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="21e79-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="21e79-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="21e79-106">no O número de referências na matriz de `rootRefIds`.</span><span class="sxs-lookup"><span data-stu-id="21e79-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="21e79-107">no Uma matriz de IDs de objeto que fazem referência a um objeto estático ou a um objeto na pilha.</span><span class="sxs-lookup"><span data-stu-id="21e79-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21e79-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="21e79-108">Remarks</span></span>  
 <span data-ttu-id="21e79-109">Tanto `RootReferences` quanto [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) são chamados para notificar o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="21e79-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="21e79-110">Os profileres normalmente implementarão um ou outro, mas não ambos, porque as informações transmitidas `RootReferences2` são um superconjunto do passado `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="21e79-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="21e79-111">É possível que a matriz de `rootRefIds` contenha um objeto nulo.</span><span class="sxs-lookup"><span data-stu-id="21e79-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="21e79-112">Por exemplo, todas as referências de objeto declaradas na pilha são tratadas como raízes pelo coletor de lixo e sempre serão relatadas.</span><span class="sxs-lookup"><span data-stu-id="21e79-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="21e79-113">As IDs de objeto retornadas por `RootReferences` não são válidas durante o próprio retorno de chamada, pois a coleta de lixo pode estar no meio da movimentação de objetos de endereços antigos para novos endereços.</span><span class="sxs-lookup"><span data-stu-id="21e79-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="21e79-114">Portanto, os profileres não devem tentar inspecionar objetos durante uma chamada de `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="21e79-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="21e79-115">Quando [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) é chamado, todos os objetos foram movidos para seus novos locais e podem ser inspecionados com segurança.</span><span class="sxs-lookup"><span data-stu-id="21e79-115">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21e79-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="21e79-116">Requirements</span></span>  
 <span data-ttu-id="21e79-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21e79-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e79-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="21e79-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21e79-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21e79-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21e79-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e79-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e79-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="21e79-121">See also</span></span>

- [<span data-ttu-id="21e79-122">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="21e79-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
