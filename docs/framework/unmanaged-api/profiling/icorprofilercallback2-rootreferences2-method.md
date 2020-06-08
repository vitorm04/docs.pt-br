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
ms.openlocfilehash: 2ce58113f40c8eb67a89b6ab6c9bb8f755975bd5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499747"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="20849-102">Método ICorProfilerCallback2::RootReferences2</span><span class="sxs-lookup"><span data-stu-id="20849-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="20849-103">Notifica o criador de perfil sobre referências de raiz após a ocorrência de uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="20849-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="20849-104">Esse método é uma extensão do método [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="20849-104">This method is an extension of the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20849-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20849-105">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20849-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="20849-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="20849-107">no O número de elementos nas `rootRefIds` `rootKinds` `rootFlags` matrizes,, e `rootIds` .</span><span class="sxs-lookup"><span data-stu-id="20849-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="20849-108">no Uma matriz de IDs de objeto, cada uma das quais faz referência a um objeto estático ou a um objeto na pilha.</span><span class="sxs-lookup"><span data-stu-id="20849-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="20849-109">Os elementos na `rootKinds` matriz fornecem informações para classificar os elementos correspondentes na `rootRefIds` matriz.</span><span class="sxs-lookup"><span data-stu-id="20849-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="20849-110">no Uma matriz de valores [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) que indicam o tipo da raiz da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="20849-110">[in] An array of [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="20849-111">no Uma matriz de valores [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) que descrevem as propriedades de uma raiz de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="20849-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="20849-112">no Uma matriz de valores UINT_PTR que apontam para um inteiro que contém informações adicionais sobre a raiz da coleta de lixo, dependendo do valor do `rootKinds` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="20849-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="20849-113">Se o tipo da raiz for uma pilha, a ID raiz será para a função que contém a variável.</span><span class="sxs-lookup"><span data-stu-id="20849-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="20849-114">Se essa ID raiz for 0, a função será uma função sem nome que é interna ao CLR.</span><span class="sxs-lookup"><span data-stu-id="20849-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="20849-115">Se o tipo da raiz for um identificador, a ID raiz será para o identificador de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="20849-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="20849-116">Para os outros tipos de raiz, a ID é um valor opaco e deve ser ignorada.</span><span class="sxs-lookup"><span data-stu-id="20849-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20849-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="20849-117">Remarks</span></span>  
 <span data-ttu-id="20849-118">As `rootRefIds` `rootKinds` matrizes,, e `rootFlags` `rootIds` são matrizes paralelas.</span><span class="sxs-lookup"><span data-stu-id="20849-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="20849-119">Ou seja,,, `rootRefIds[i]` `rootKinds[i]` `rootFlags[i]` e `rootIds[i]` todas as preocupações com a mesma raiz.</span><span class="sxs-lookup"><span data-stu-id="20849-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="20849-120">Ambos `RootReferences` e `RootReferences2` são chamados para notificar o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="20849-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="20849-121">Os profileres normalmente implementarão um método ou o outro, mas não ambos, porque as informações transmitidas `RootReferences2` são um superconjunto do passado `RootReferences` .</span><span class="sxs-lookup"><span data-stu-id="20849-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="20849-122">É possível que as entradas no `rootRefIds` sejam zero, o que implica que a referência raiz correspondente é nula e não se refere a um objeto no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="20849-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="20849-123">As IDs de objeto retornadas por `RootReferences2` não são válidas durante o próprio retorno de chamada, pois a coleta de lixo pode estar no meio da movimentação de objetos de endereços antigos para novos endereços.</span><span class="sxs-lookup"><span data-stu-id="20849-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="20849-124">Portanto, os criadores de perfis não devem tentar inspecionar objetos durante uma chamada `RootReferences2`.</span><span class="sxs-lookup"><span data-stu-id="20849-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="20849-125">Quando [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) é chamado, todos os objetos foram movidos para seus novos locais e podem ser inspecionados com segurança.</span><span class="sxs-lookup"><span data-stu-id="20849-125">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20849-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="20849-126">Requirements</span></span>  
 <span data-ttu-id="20849-127">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20849-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20849-128">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="20849-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="20849-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20849-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20849-130">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20849-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20849-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="20849-131">See also</span></span>

- [<span data-ttu-id="20849-132">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="20849-132">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="20849-133">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="20849-133">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
