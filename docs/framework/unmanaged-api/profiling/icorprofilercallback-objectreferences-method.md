---
title: Método ICorProfilerCallback::ObjectReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9659f37f0ae9297837dbc4b1602cb00b8eff2fd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471440"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="84c07-102">Método ICorProfilerCallback::ObjectReferences</span><span class="sxs-lookup"><span data-stu-id="84c07-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="84c07-103">Notifica o criador de perfil sobre os objetos na memória que está sendo referenciado pelo objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="84c07-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84c07-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84c07-104">Syntax</span></span>  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="84c07-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="84c07-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="84c07-106">[in] A ID do objeto que faz referência a objetos.</span><span class="sxs-lookup"><span data-stu-id="84c07-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="84c07-107">[in] A ID da classe que o objeto especificado é uma instância do.</span><span class="sxs-lookup"><span data-stu-id="84c07-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="84c07-108">[in] O número de objetos referenciados pelo objeto especificado (ou seja, o número de elementos no `objectRefIds` matriz).</span><span class="sxs-lookup"><span data-stu-id="84c07-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="84c07-109">[in] Uma matriz de IDs de objetos que estão sendo referenciadas por `objectId`.</span><span class="sxs-lookup"><span data-stu-id="84c07-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84c07-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="84c07-110">Remarks</span></span>  
 <span data-ttu-id="84c07-111">O `ObjectReferences` método é chamado para cada objeto restante no heap após uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="84c07-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="84c07-112">Se o criador de perfil retornará um erro desse retorno de chamada, os serviços de criação de perfil serão Descontinuado invocar esse retorno de chamada até a próxima coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="84c07-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="84c07-113">O `ObjectReferences` retorno de chamada pode ser usado em conjunto com o [ICorProfilerCallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) retorno de chamada para criar um gráfico de referência de objeto completo para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="84c07-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="84c07-114">O common language runtime (CLR) garante que cada referência de objeto é relatada somente uma vez pelo `ObjectReferences` método.</span><span class="sxs-lookup"><span data-stu-id="84c07-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="84c07-115">As IDs de objeto retornado por `ObjectReferences` não são válidos durante o retorno de chamada em si, porque a coleta de lixo pode estar no meio de movimentação de objetos.</span><span class="sxs-lookup"><span data-stu-id="84c07-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="84c07-116">Portanto, os criadores de perfis não devem tentar inspecionar objetos durante um `ObjectReferences` chamar.</span><span class="sxs-lookup"><span data-stu-id="84c07-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="84c07-117">Quando [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) é chamado, o lixo coleção for concluída e a inspeção pode ser feita com segurança.</span><span class="sxs-lookup"><span data-stu-id="84c07-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="84c07-118">Um valor nulo `ClassId` indica que `objectId` tem um tipo que está descarregando.</span><span class="sxs-lookup"><span data-stu-id="84c07-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84c07-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="84c07-119">Requirements</span></span>  
 <span data-ttu-id="84c07-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84c07-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84c07-121">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="84c07-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84c07-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84c07-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84c07-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84c07-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84c07-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84c07-124">See also</span></span>
- [<span data-ttu-id="84c07-125">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="84c07-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
