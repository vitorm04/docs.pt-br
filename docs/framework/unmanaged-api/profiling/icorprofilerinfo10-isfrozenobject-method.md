---
title: 'ICorProfilerInfo10:: iscongeladoobject'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: b6dabefceba038a129148f7ba36d4ffcfc425c80
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790034"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="cf762-102">Método ICorProfilerInfo10:: iscongeladoobject</span><span class="sxs-lookup"><span data-stu-id="cf762-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="cf762-103">Dado um ObjectID, determina se o objeto está em um segmento somente leitura.</span><span class="sxs-lookup"><span data-stu-id="cf762-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="cf762-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf762-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="cf762-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf762-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="cf762-106">\[em] o objeto a ser examinado.</span><span class="sxs-lookup"><span data-stu-id="cf762-106">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="cf762-107">\[out] uma `BOOL` indicando se o objeto está em um segmento somente leitura.</span><span class="sxs-lookup"><span data-stu-id="cf762-107">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="cf762-108">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="cf762-108">Requirements</span></span>

<span data-ttu-id="cf762-109">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="cf762-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="cf762-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cf762-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="cf762-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf762-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="cf762-112">**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf762-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cf762-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="cf762-113">See also</span></span>

- [<span data-ttu-id="cf762-114">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="cf762-114">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
