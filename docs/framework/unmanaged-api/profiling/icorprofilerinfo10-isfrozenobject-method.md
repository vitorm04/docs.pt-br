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
ms.openlocfilehash: 21f9cb415f913a9c865a487f6e80523344db811e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452182"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="26029-102">Método ICorProfilerInfo10:: iscongeladoobject</span><span class="sxs-lookup"><span data-stu-id="26029-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="26029-103">Dado um ObjectID, determina se o objeto está em um segmento somente leitura.</span><span class="sxs-lookup"><span data-stu-id="26029-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="26029-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26029-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="26029-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="26029-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="26029-106">\[em] o objeto a ser examinado.</span><span class="sxs-lookup"><span data-stu-id="26029-106">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="26029-107">\[out] uma `BOOL` indicando se o objeto está em um segmento somente leitura.</span><span class="sxs-lookup"><span data-stu-id="26029-107">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="26029-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26029-108">Requirements</span></span>

<span data-ttu-id="26029-109">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="26029-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="26029-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="26029-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="26029-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26029-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="26029-112">**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26029-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="26029-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="26029-113">See also</span></span>

- [<span data-ttu-id="26029-114">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="26029-114">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
