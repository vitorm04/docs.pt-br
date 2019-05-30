---
title: ICorProfilerCallback5::Método ConditionalWeakTableElementReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5.ConditionalWeakTableReferences
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ConditionalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08b35dd1744dbbb64d202718b61a9db5684d3bc3
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380355"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="c45e4-102">ICorProfilerCallback5::Método ConditionalWeakTableElementReferences</span><span class="sxs-lookup"><span data-stu-id="c45e4-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>

<span data-ttu-id="c45e4-103">Identifica o fechamento transitivo de objetos referenciados por estas raízes por meio de referências diretas do campo de membro e de dependências `ConditionalWeakTable`.</span><span class="sxs-lookup"><span data-stu-id="c45e4-103">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>

## <a name="syntax"></a><span data-ttu-id="c45e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c45e4-104">Syntax</span></span>

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a><span data-ttu-id="c45e4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c45e4-105">Parameters</span></span>

`cRootRefs`\
<span data-ttu-id="c45e4-106">[in] O número de elementos nas matrizes `keyRefIds`, `valueRefIds` e `rootIds`.</span><span class="sxs-lookup"><span data-stu-id="c45e4-106">[in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>

`keyRefIds`\
<span data-ttu-id="c45e4-107">[in] Uma matriz de IDs de objeto, cada uma contendo o `ObjectID` para o elemento principal do par do identificador dependente.</span><span class="sxs-lookup"><span data-stu-id="c45e4-107">[in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>

`valueRefIds`\
<span data-ttu-id="c45e4-108">[in] Uma matriz de IDs de objeto, cada uma contendo o `ObjectID` para o elemento secundário do par do identificador dependente.</span><span class="sxs-lookup"><span data-stu-id="c45e4-108">[in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="c45e4-109">(`keyRefIds[i]` mantém `valueRefIds[i]` ativo.)</span><span class="sxs-lookup"><span data-stu-id="c45e4-109">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>

`rootIds`\
<span data-ttu-id="c45e4-110">[in] Uma matriz de valores `GCHandleID` que apontam para um número inteiro que contém informações adicionais sobre a raiz de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c45e4-110">[in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>

<span data-ttu-id="c45e4-111">Nenhum dos valores `ObjectID` retornados pelo método `ConditionalWeakTableElementReferences` é válido durante o retorno de chamada em si, porque o coletor de lixo pode estar no processo de mover objetos de locais antigos para novos.</span><span class="sxs-lookup"><span data-stu-id="c45e4-111">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="c45e4-112">Portanto, os criadores de perfis não devem tentar inspecionar objetos durante uma chamada `ConditionalWeakTableElementReferences`.</span><span class="sxs-lookup"><span data-stu-id="c45e4-112">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="c45e4-113">Ao `GarbageCollectionFinished`, todos os objetos foram movidos para os novos locais e a inspeção pode ser feita.</span><span class="sxs-lookup"><span data-stu-id="c45e4-113">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>

## <a name="example"></a><span data-ttu-id="c45e4-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c45e4-114">Example</span></span>

<span data-ttu-id="c45e4-115">O exemplo de código a seguir demonstra como implementar [ICorProfilerCallback5](icorprofilercallback5-interface.md) e usar esse método.</span><span class="sxs-lookup"><span data-stu-id="c45e4-115">The following code example demonstrates how to implement [ICorProfilerCallback5](icorprofilercallback5-interface.md) and use this method.</span></span>

```cpp
HRESULT Callback5Impl::ConditionalWeakTableElementReferences(
    ULONG      cRootRefs,
    ObjectID   keyRefIds[],
    ObjectID   valueRefIds[],
    GCHandleID rootIds[])
{
    printf("Callback5Impl::ConditionalWeakTableElementReferences called\n");
    for (unsigned int i = 0; i < cRootRefs; ++i)
    {
        // Save dependency to XML for later retrieval
        PersistDependencyToXml(rootIds[i], keyRefIds[i], valueRefIds[i]);
        // or store dependency to an internal map
        m_cwt_deps->add_dep(rootIds[i], keyRefIds[i], valueRefIds[i]);
        // or add arc to object graph
        m_obj_graph->add_arc(keyRefIds[i], valueRefIds[i], rootIds[i]);
    }
    return S_OK;
}
```

## <a name="remarks"></a><span data-ttu-id="c45e4-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="c45e4-116">Remarks</span></span>

<span data-ttu-id="c45e4-117">Um criador de perfil para o .NET Framework 4.5 ou versões posteriores implementa a [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface e registra as dependências especificadas pelo `ConditionalWeakTableElementReferences` método.</span><span class="sxs-lookup"><span data-stu-id="c45e4-117">A profiler for the .NET Framework 4.5 or later versions implements the [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="c45e4-118">`ICorProfilerCallback5` fornece o conjunto completo de dependências entre objetos ativos representados pelas `ConditionalWeakTable` entradas.</span><span class="sxs-lookup"><span data-stu-id="c45e4-118">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="c45e4-119">Essas dependências e o membro de campo referências especificadas pelo [ICorProfilerCallback:: Objectreferences](icorprofilercallback-objectreferences-method.md) método habilitar um criador de perfil gerenciado gerar o grafo de objeto completo de objetos em tempo real.</span><span class="sxs-lookup"><span data-stu-id="c45e4-119">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>

## <a name="requirements"></a><span data-ttu-id="c45e4-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c45e4-120">Requirements</span></span>

<span data-ttu-id="c45e4-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c45e4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="c45e4-122">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c45e4-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="c45e4-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c45e4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c45e4-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c45e4-124">See also</span></span>

- [<span data-ttu-id="c45e4-125">Interface ICorProfilerCallback5</span><span class="sxs-lookup"><span data-stu-id="c45e4-125">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)
