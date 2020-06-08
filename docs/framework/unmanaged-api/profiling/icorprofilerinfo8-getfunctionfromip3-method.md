---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 6822757608429ca5f4ef9520ab7574d440b67b26
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495250"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="ea026-102">Método ICorProfilerInfo8:: GetFunctionFromIP3</span><span class="sxs-lookup"><span data-stu-id="ea026-102">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>

<span data-ttu-id="ea026-103">Mapeia um ponteiro de instrução de código gerenciado para uma FunctionID.</span><span class="sxs-lookup"><span data-stu-id="ea026-103">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="ea026-104">Esse método funciona para métodos dinâmicos e não dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="ea026-104">This method works for both dynamic and non-dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="ea026-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea026-105">Syntax</span></span>

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a><span data-ttu-id="ea026-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ea026-106">Parameters</span></span>

- `ip`

  <span data-ttu-id="ea026-107">\[in] o ponteiro de instrução no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ea026-107">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="ea026-108">\[out] a ID da função.</span><span class="sxs-lookup"><span data-stu-id="ea026-108">\[out] The function ID.</span></span>

- `pReJitId`

  <span data-ttu-id="ea026-109">\[out] a identidade da versão recompilada do JIT da função.</span><span class="sxs-lookup"><span data-stu-id="ea026-109">\[out] The identity of the JIT-recompiled version of the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea026-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea026-110">Remarks</span></span>

<span data-ttu-id="ea026-111">Esse método funciona para métodos dinâmicos e não dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="ea026-111">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="ea026-112">É um superconjunto de [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), que funciona apenas para funções com metadados.</span><span class="sxs-lookup"><span data-stu-id="ea026-112">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="ea026-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea026-113">Requirements</span></span>

<span data-ttu-id="ea026-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea026-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ea026-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ea026-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="ea026-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea026-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="ea026-117">**.NET Framework versões:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ea026-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ea026-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="ea026-118">See also</span></span>

- [<span data-ttu-id="ea026-119">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="ea026-119">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
