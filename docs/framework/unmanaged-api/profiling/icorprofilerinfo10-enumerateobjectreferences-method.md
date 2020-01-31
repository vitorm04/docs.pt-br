---
title: ICorProfilerInfo10::EnumerateObjectReferences
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7fd62e0d3d9173f3b75882131e57126075c0677f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863303"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="628d4-102">Método ICorProfilerInfo10:: EnumerateObjectReferences</span><span class="sxs-lookup"><span data-stu-id="628d4-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="628d4-103">Dado um ObjectID, retorno de chamada e clientData, enumera cada referência de objeto (se houver).</span><span class="sxs-lookup"><span data-stu-id="628d4-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="628d4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="628d4-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="628d4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="628d4-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="628d4-106">\[em] o objeto no qual enumerar referências.</span><span class="sxs-lookup"><span data-stu-id="628d4-106">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="628d4-107">\[em] a função que será chamada com as referências para o objeto.</span><span class="sxs-lookup"><span data-stu-id="628d4-107">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="628d4-108">\[em] dados fornecidos pelo Profiler para passar para a função `callback`.</span><span class="sxs-lookup"><span data-stu-id="628d4-108">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="628d4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="628d4-109">Remarks</span></span>

<span data-ttu-id="628d4-110">O método `EnumerateObjectReferences` é semelhante a [ObjectReferences](icorprofilercallback-objectreferences-method.md), exceto pelo fato de que ele percorre as referências sob demanda para o criador de perfil em vez de alocar previamente uma matriz para armazenar as referências.</span><span class="sxs-lookup"><span data-stu-id="628d4-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="628d4-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="628d4-111">Requirements</span></span>

<span data-ttu-id="628d4-112">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="628d4-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="628d4-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="628d4-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="628d4-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="628d4-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="628d4-115">**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="628d4-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="628d4-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="628d4-116">See also</span></span>

- [<span data-ttu-id="628d4-117">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="628d4-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
