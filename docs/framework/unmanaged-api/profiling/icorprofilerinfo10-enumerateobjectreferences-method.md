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
ms.openlocfilehash: d6518612c213d21c2dc7d80878121ccd3b7e2abb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449856"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="c7b4b-102">Método ICorProfilerInfo10:: EnumerateObjectReferences</span><span class="sxs-lookup"><span data-stu-id="c7b4b-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="c7b4b-103">Dado um ObjectID, retorno de chamada e clientData, enumera cada referência de objeto (se houver).</span><span class="sxs-lookup"><span data-stu-id="c7b4b-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="c7b4b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7b4b-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

#### <a name="parameters"></a><span data-ttu-id="c7b4b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7b4b-105">Parameters</span></span>

`objectId` \
<span data-ttu-id="c7b4b-106">no O objeto no qual enumerar referências.</span><span class="sxs-lookup"><span data-stu-id="c7b4b-106">[in] The object to enumerate references on.</span></span>

`callback` \
<span data-ttu-id="c7b4b-107">no A função que será chamada com as referências para o objeto.</span><span class="sxs-lookup"><span data-stu-id="c7b4b-107">[in] The function that will be called with the references for the object.</span></span>

`clientData` \
<span data-ttu-id="c7b4b-108">no Dados fornecidos pelo criador de perfil para passar para a função `callback`.</span><span class="sxs-lookup"><span data-stu-id="c7b4b-108">[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7b4b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c7b4b-109">Remarks</span></span>

<span data-ttu-id="c7b4b-110">O método `EnumerateObjectReferences` é semelhante a [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), exceto pelo fato de que ele percorre as referências sob demanda para o criador de perfil em vez de alocar previamente uma matriz para armazenar as referências.</span><span class="sxs-lookup"><span data-stu-id="c7b4b-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7b4b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7b4b-111">Requirements</span></span>

<span data-ttu-id="c7b4b-112">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="c7b4b-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="c7b4b-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c7b4b-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="c7b4b-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7b4b-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c7b4b-115">**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7b4b-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c7b4b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7b4b-116">See also</span></span>

- [<span data-ttu-id="c7b4b-117">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="c7b4b-117">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
