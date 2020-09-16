---
title: ICorProfilerInfo10::SuspendRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.SuspendRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 121ed0401628193f6e2fe632a124c08aad7bd1b4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551433"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="58fec-102">Método ICorProfilerInfo10:: SuspendRuntime</span><span class="sxs-lookup"><span data-stu-id="58fec-102">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="58fec-103">Suspende o tempo de execução sem executar um GC.</span><span class="sxs-lookup"><span data-stu-id="58fec-103">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="58fec-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="58fec-104">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="58fec-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58fec-105">Requirements</span></span>

<span data-ttu-id="58fec-106">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="58fec-106">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="58fec-107">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="58fec-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="58fec-108">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58fec-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="58fec-109">**Versões do .net:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58fec-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="58fec-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="58fec-110">See also</span></span>

- [<span data-ttu-id="58fec-111">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="58fec-111">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
