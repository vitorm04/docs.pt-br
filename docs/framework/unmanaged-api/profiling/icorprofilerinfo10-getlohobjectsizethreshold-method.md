---
title: ICorProfilerInfo10::GetLOHObjectSizeThreshold
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 280f0a401f87f81e1ef9d4a2c85c06599442b5ec
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543940"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="c9456-102">Método ICorProfilerInfo10:: GetLOHObjectSizeThreshold</span><span class="sxs-lookup"><span data-stu-id="c9456-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="c9456-103">Obtém o valor do limite de LOH (heap de objeto grande) configurado.</span><span class="sxs-lookup"><span data-stu-id="c9456-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="c9456-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9456-104">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="c9456-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9456-105">Parameters</span></span>

- `pThreshold`

  <span data-ttu-id="c9456-106">\[out] o limite de heap de objeto grande em bytes.</span><span class="sxs-lookup"><span data-stu-id="c9456-106">\[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9456-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9456-107">Remarks</span></span>

<span data-ttu-id="c9456-108">Os objetos maiores que o limite de heap de objeto grande serão alocados no heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="c9456-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="c9456-109">A partir do .NET Core 3,0, o limite de heap de objeto grande é configurável, conterá `pThreshold` o tamanho limite de heap de objeto grande ativo em bytes.</span><span class="sxs-lookup"><span data-stu-id="c9456-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="c9456-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9456-110">Requirements</span></span>

<span data-ttu-id="c9456-111">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="c9456-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="c9456-112">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c9456-112">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="c9456-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9456-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c9456-114">**Versões do .net:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9456-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c9456-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="c9456-115">See also</span></span>

- [<span data-ttu-id="c9456-116">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="c9456-116">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
