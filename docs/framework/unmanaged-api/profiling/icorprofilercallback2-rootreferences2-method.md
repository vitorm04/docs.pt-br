---
title: Método ICorProfilerCallback2::RootReferences2
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09616243aef272be041573864effd25017cc65c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082146"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="126e4-102">Método ICorProfilerCallback2::RootReferences2</span><span class="sxs-lookup"><span data-stu-id="126e4-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="126e4-103">Notifica o criador de perfil sobre referências raiz após a ocorrência de uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="126e4-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="126e4-104">Esse método é uma extensão de [ICorProfilerCallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="126e4-104">This method is an extension of the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="126e4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="126e4-105">Syntax</span></span>  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="126e4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="126e4-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="126e4-107">[in] O número de elementos na `rootRefIds`, `rootKinds`, `rootFlags`, e `rootIds` matrizes.</span><span class="sxs-lookup"><span data-stu-id="126e4-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="126e4-108">[in] Uma matriz de IDs de objeto, cada um deles faz referência a um objeto estático ou um objeto na pilha.</span><span class="sxs-lookup"><span data-stu-id="126e4-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="126e4-109">Elementos na `rootKinds` matriz fornecem informações para classificar os elementos correspondentes no `rootRefIds` matriz.</span><span class="sxs-lookup"><span data-stu-id="126e4-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="126e4-110">[in] Uma matriz de [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) valores que indicam o tipo de raiz de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="126e4-110">[in] An array of [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="126e4-111">[in] Uma matriz de [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) valores que descrevem as propriedades de uma raiz de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="126e4-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="126e4-112">[in] Uma matriz de UINT_PTR valores que apontam para um inteiro que contém informações adicionais sobre a raiz de coleta de lixo, dependendo do valor da `rootKinds` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="126e4-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="126e4-113">Se o tipo da raiz é uma pilha, a ID de raiz é para a função que contém a variável.</span><span class="sxs-lookup"><span data-stu-id="126e4-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="126e4-114">Se essa ID de raiz for 0, a função é uma função sem nome que é interna ao CLR.</span><span class="sxs-lookup"><span data-stu-id="126e4-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="126e4-115">Se o tipo da raiz é um identificador, a ID da raiz é o identificador da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="126e4-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="126e4-116">Para outros tipos de raiz, a ID é um valor opaco e deve ser ignorada.</span><span class="sxs-lookup"><span data-stu-id="126e4-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="126e4-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="126e4-117">Remarks</span></span>  
 <span data-ttu-id="126e4-118">O `rootRefIds`, `rootKinds`, `rootFlags`, e `rootIds` matrizes são matrizes paralelas.</span><span class="sxs-lookup"><span data-stu-id="126e4-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="126e4-119">Ou seja, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, e `rootIds[i]` todos dizem respeito a mesma raiz.</span><span class="sxs-lookup"><span data-stu-id="126e4-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="126e4-120">Ambos `RootReferences` e `RootReferences2` são chamados para notificar o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="126e4-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="126e4-121">Criadores de perfil serão normalmente implementam um método ou a outra, mas não ambos, porque as informações passadas `RootReferences2` é um superconjunto do que passado `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="126e4-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="126e4-122">É possível que as entradas no `rootRefIds` como zero, o que implica que a referência raiz correspondente é nula e não faz referência a um objeto no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="126e4-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="126e4-123">As IDs de objeto retornado por `RootReferences2` não são válidos durante o retorno de chamada em si, porque a coleta de lixo pode estar no meio de mover objetos de endereços antigos para novos endereços.</span><span class="sxs-lookup"><span data-stu-id="126e4-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="126e4-124">Portanto, os criadores de perfis não devem tentar inspecionar objetos durante uma chamada `RootReferences2`.</span><span class="sxs-lookup"><span data-stu-id="126e4-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="126e4-125">Quando [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) é chamado, todos os objetos foram movidos para os novos locais e pode ser inspecionados com segurança.</span><span class="sxs-lookup"><span data-stu-id="126e4-125">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="126e4-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="126e4-126">Requirements</span></span>  
 <span data-ttu-id="126e4-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="126e4-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="126e4-128">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="126e4-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="126e4-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="126e4-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="126e4-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="126e4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="126e4-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="126e4-131">See also</span></span>

- [<span data-ttu-id="126e4-132">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="126e4-132">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="126e4-133">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="126e4-133">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
