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
ms.openlocfilehash: 6d50a5d74eccff6fe39aca111f768bac4d8f2e2e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868324"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="ecea2-102">Método ICorProfilerInfo8:: GetFunctionFromIP3</span><span class="sxs-lookup"><span data-stu-id="ecea2-102">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>

<span data-ttu-id="ecea2-103">Mapeia um ponteiro de instrução de código gerenciado para uma FunctionID.</span><span class="sxs-lookup"><span data-stu-id="ecea2-103">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="ecea2-104">Esse método funciona para métodos dinâmicos e não dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="ecea2-104">This method works for both dynamic and non-dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="ecea2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ecea2-105">Syntax</span></span>

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a><span data-ttu-id="ecea2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ecea2-106">Parameters</span></span>

- `ip`

  <span data-ttu-id="ecea2-107">\[in] o ponteiro de instrução no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ecea2-107">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="ecea2-108">\[out] a ID da função.</span><span class="sxs-lookup"><span data-stu-id="ecea2-108">\[out] The function ID.</span></span>

- `pReJitId`

  <span data-ttu-id="ecea2-109">\[out] a identidade da versão recompilada do JIT da função.</span><span class="sxs-lookup"><span data-stu-id="ecea2-109">\[out] The identity of the JIT-recompiled version of the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="ecea2-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ecea2-110">Remarks</span></span>

<span data-ttu-id="ecea2-111">Esse método funciona para métodos dinâmicos e não dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="ecea2-111">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="ecea2-112">É um superconjunto de [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), que funciona apenas para funções com metadados.</span><span class="sxs-lookup"><span data-stu-id="ecea2-112">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="ecea2-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ecea2-113">Requirements</span></span>

<span data-ttu-id="ecea2-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecea2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="ecea2-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ecea2-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="ecea2-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ecea2-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="ecea2-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ecea2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ecea2-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="ecea2-118">See also</span></span>

- [<span data-ttu-id="ecea2-119">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="ecea2-119">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
