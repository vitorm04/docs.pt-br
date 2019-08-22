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
ms.openlocfilehash: d212c06c7ddc9f22095c0b95f19fd1083482435c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661231"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="a14b8-102">Método ICorProfilerInfo10:: iscongeladoobject</span><span class="sxs-lookup"><span data-stu-id="a14b8-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="a14b8-103">Dado um ObjectID, determina se o objeto está em um segmento somente leitura.</span><span class="sxs-lookup"><span data-stu-id="a14b8-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="a14b8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a14b8-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

#### <a name="parameters"></a><span data-ttu-id="a14b8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a14b8-105">Parameters</span></span>

`objectId` \
<span data-ttu-id="a14b8-106">no O objeto a ser examinado.</span><span class="sxs-lookup"><span data-stu-id="a14b8-106">[in] The object to examine.</span></span>

`pbFrozen` \
<span data-ttu-id="a14b8-107">fora Um `BOOL` que indica se o objeto está em um segmento somente leitura.</span><span class="sxs-lookup"><span data-stu-id="a14b8-107">[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="a14b8-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a14b8-108">Requirements</span></span>

<span data-ttu-id="a14b8-109">**Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="a14b8-109">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="a14b8-110">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a14b8-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="a14b8-111">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a14b8-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a14b8-112">**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a14b8-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a14b8-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a14b8-113">See also</span></span>

- [<span data-ttu-id="a14b8-114">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="a14b8-114">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
