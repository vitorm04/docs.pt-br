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
ms.openlocfilehash: 3755260b885768de6b5b2d6342c0ad590a95caff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548664"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="53bf8-102">Método ICorProfilerInfo10:: iscongeladoobject</span><span class="sxs-lookup"><span data-stu-id="53bf8-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="53bf8-103">Dado um ObjectID, determina se o objeto está em um segmento somente leitura.</span><span class="sxs-lookup"><span data-stu-id="53bf8-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="53bf8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53bf8-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="53bf8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="53bf8-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="53bf8-106">\[no] o objeto a ser examinado.</span><span class="sxs-lookup"><span data-stu-id="53bf8-106">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="53bf8-107">\[out] um `BOOL` que indica se o objeto está em um segmento somente leitura.</span><span class="sxs-lookup"><span data-stu-id="53bf8-107">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="53bf8-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53bf8-108">Requirements</span></span>

<span data-ttu-id="53bf8-109">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="53bf8-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="53bf8-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="53bf8-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="53bf8-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53bf8-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="53bf8-112">**Versões do .net:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53bf8-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="53bf8-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="53bf8-113">See also</span></span>

- [<span data-ttu-id="53bf8-114">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="53bf8-114">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
